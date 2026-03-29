---
name: validate-artifacts
description: >-
  Reviews PRDs, plans, tasks, architecture markdown, ADRs, LTI deliverables,
  and prompt logs for completeness, consistency, paths, and traceability. Default
  procedure for documentation-auditor and any cross-doc validation. Does not
  replace human sign-off; produces an evidence-based findings report.
---

# Validate artifacts (cross-document review)

## Purpose

Provide a **repeatable** validation pass over design-repo artifacts so teams catch **missing sections**, **contradictions**, **naming drift**, and **ungrounded decisions** before they harden into false confidence.

## When to Use

- Before treating a milestone as “done” (course submit, design review, handoff).
- After **merging** content from PRD into the consolidated deliverable **`LTI-<CONTRIBUTOR-SLUG>/LTI-<CONTRIBUTOR-SLUG>.md`**, or after parallel agent edits.
- When the user suspects **two documents disagree** (e.g. FR vs diagram vs ADR).
- After applying **generate-prd** or **develop-architect** to verify outputs meet this repo’s conventions.

## When Not to Use

- As a substitute for **legal/compliance** review or **security** assessment.
- To **rewrite** product intent or architecture—this skill **flags** issues; owners fix them (or an explicit follow-up skill/agent run applies changes).
- When the user only wants a **quick typo check**—still valid, but say you are doing a **lightweight** pass and skip non-applicable checks.

## Inputs

Collect what the user points at (paths relative to repo root). Typical sets:

| Kind | Path pattern (see conventions below) |
|------|--------------------------------------|
| PRD | `LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md` |
| Plan | `ai-specs/plan/<NNN>-plan.md` |
| Task | `ai-specs/tasks/<NNN>-task.md` |
| ADR log | `LTI-<CONTRIBUTOR-SLUG>/ADR.md` |
| User stories backlog | `LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md` |
| Consolidated course doc | `LTI-<CONTRIBUTOR-SLUG>/LTI-<CONTRIBUTOR-SLUG>.md` |
| Prompt log (structure / append-only) | `LTI-<CONTRIBUTOR-SLUG>/prompts.md` — per **`.cursor/rules/30-prompt-tracking.mdc`** when assessing course submission hygiene |
| Optional persisted review | Output path below |

**Minimum:** at least **one** substantive artifact, or explicit permission to scan under **`ai-specs/`** (all subfolders) and under every **`LTI-*/`** contributor folder at repository root.

## Outputs

1. **Primary:** A structured **findings report** in the assistant reply, using the sections below (use `PASS` / `FAIL` / `N/A` per check where helpful).
2. **Optional persisted log:** If the user asks to save the review, write **`ai-specs/review/<NNN>-review.md`** where:
   - **`<NNN>`** is the next three-digit zero-padded integer for files matching `^\d{3}-review\.md$` under `ai-specs/review/` (start at `001`, create directory if missing).
   - The file contains the same report body plus **Reviewed paths** and **Date (UTC)**.

### Report structure (required)

```markdown
# Validation report

## Summary
- Verdict: Pass | Pass with findings | Blocked
- Artifacts reviewed: <list paths>

## Completeness
<!-- mandatory sections / expected headings per artifact type -->

## Internal consistency
<!-- single-document contradictions, duplicate headings, broken numbering -->

## Cross-artifact consistency
<!-- PRD vs LTI doc vs diagrams vs ADRs vs plans/tasks -->

## Conventions and paths
<!-- filenames, slugs, Mermaid fences, ADR format; diagram semantics per .cursor/rules/50-diagram-standards.mdc when diagrams exist -->

## Evidence vs assumptions
<!-- where product claims lack validation hooks -->

## Architecture grounded in requirements
<!-- ADRs/HLD vs FRs/NFRs/goals -->

## Backlog quality (when UserStories-*.md in scope)
<!-- INVEST, BDD, decomposition, prioritization, estimation, story structure, backlog-to-PRD alignment -->

## Recommended actions
<!-- numbered, each actionable; no silent rewrites of intent -->
```

## Process

1. **Inventory** — List exact files you read; if a referenced path is missing, record it as **FAIL** (missing artifact).
2. **Completeness** — Against the templates in **generate-prd** and **develop-architect** (as applicable), verify **expected sections exist**. For **`ai-specs/plan/<NNN>-plan.md`** and **`ai-specs/tasks/<NNN>-task.md`** (when in scope), verify **path naming** per **`.cursor/rules/40-naming-and-paths.mdc`** and that headings/content are **internally coherent**—this repo revision has **no** mandatory section template for those file types. Treat optional sections as **N/A** only if the artifact type truly does not need them (e.g. tiny plan).
3. **Internal consistency** — Same term for the same concept; no duplicate **H1**; **FR-** / **ADR-** numbering monotonic where used; no conflicting MVP definitions inside one file.
4. **Cross-artifact** — Trace **goals → FRs → metrics** (PRD); **FRs ↔ diagrams** (entities/flows named consistently); **NFRs ↔ architecture** (e.g. latency claim vs sync chain); **ADRs** reference forces that appear in PRD/NFRs or are labeled **assumption**.
5. **Conventions** — PRD at **`LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md`** (regex `^\d{3}-prd\.md$` in that folder); plans/tasks at **`ai-specs/plan/<NNN>-plan.md`**, **`ai-specs/tasks/<NNN>-task.md`** (regex `^\d{3}-(plan|task)\.md$`); contributor main doc **`LTI-<CONTRIBUTOR-SLUG>/LTI-<CONTRIBUTOR-SLUG>.md`** basename matches folder; Mermaid blocks fenced with **`mermaid`**. Where diagrams exist, flag violations of **`.cursor/rules/50-diagram-standards.mdc`** (naming across diagrams, C4 level discipline, unsupported components).
6. **Prompt log** — Apply this check in two cases:
   - **Explicit:** `LTI-<CONTRIBUTOR-SLUG>/prompts.md` was listed as an input; or
   - **Implied:** any `LTI-<CONTRIBUTOR-SLUG>/` artifact is in scope and the review is submission-ready (the user mentions "submission", "complete", "ready to submit", or **`.cursor/rules/60-review-and-validation.mdc`** requires a validation pass).
   In either case, compute the implied path `LTI-<CONTRIBUTOR-SLUG>/prompts.md` from the active contributor slug (derived from the folder of any `LTI-*` artifact in scope). Then:
   - **Missing file:** record as **FAIL** with the exact expected path.
   - **Present file:** check (a) first line is `# Prompts log`, (b) every entry uses the `## Prompt - <YYYY-MM-DDTHH:mm:ssZ>` / `### Agent:` heading pair, (c) entries after the first are separated by a line containing only `---`, and (d) no `# Prompts log` header is duplicated mid-file — per **`.cursor/rules/30-prompt-tracking.mdc`**. Record each structural violation as **FAIL** with file path and line reference. Do not audit prompt *content* for product truth.
7. **Evidence vs assumptions** — Flag marketing or compliance claims without **Open questions**, **Assumptions**, or cited source.
8. **Architecture vs requirements** — Flag ADRs or containers that introduce **new product scope** not traceable to PRD/**`ReadMe.md`**/user instruction.
9. **Backlog validation** (when **`UserStories-*.md`** is in scope) — Apply the **Backlog validation** checklist from **`.cursor/agents/documentation-auditor.md`**: INVEST compliance, epic decomposition quality, BDD acceptance criteria (Given/When/Then with happy + edge cases), seven-factor prioritization with justification, Fibonacci estimation realism, story structure (Additional notes, Related stories, FR traceability), backlog sort order (P0 first), and backlog-to-PRD alignment. Report each subsection as PASS / FAIL / N/A.
10. **Verdict** — **Blocked** if any **integrity** issue (wrong overwrite, duplicate file for same intent, contradictory “source of truth”). **Pass with findings** if issues are fixable without renegotiating intent.

**Governance alignment:** Cross-check applicable **`.cursor/rules/`** (`20-`, `30-`, `40-`, `50-`, `60-`) when the validation scope includes those topics; **`.cursor/rules/60-review-and-validation.mdc`** requires a validation pass before “complete” / submission-ready claims.

## Quality Checks

| Check | Pass criteria |
|-------|----------------|
| Completeness | All mandatory sections for each in-scope artifact type are present or explicitly marked out-of-scope with reason. |
| No silent contradictions | Conflicts are listed with **file + heading** citations, not “fixed” by merging without user direction. |
| Traceability | Main user flows and data entities appear under consistent names across PRD, use cases, diagrams, and tasks. |
| ADR hygiene | New decisions are **appended**; supersessions link **ADR-NNN** targets; no blank placeholder ADRs. |
| Path hygiene | No ambiguous stems like bare `-prd.md` / `-plan.md` / `-task.md`; numeric **`NNN`** is three-digit. |

**Bad output:** Vague praise (“looks good”), no file paths, or rewritten requirements that resolve contradictions without logging them.

**Good output:** Enumerated findings, each with **location**, **severity** (blocker / major / minor), and **suggested next step** (which skill or owner).

## Create vs Update Guidance

- **Create** a new review file only when the user asks to **persist** results; otherwise reply in chat only.
- **Update** an existing `*-review.md` only if the user asks to **revise that report**; otherwise create the **next** `<NNN>-review.md` to preserve history.
- **Do not** modify PRD/plan/task/source deliverables **inside this skill** unless the user explicitly asks you to apply fixes after the review.

## Common Mistakes to Avoid

- Reviewing only one artifact when the user’s question is **cross-cutting** (always state scope limits).
- Treating **Mermaid syntax errors** as optional—list them; they break rendered docs.
- Confusing **conceptual** data model (PRD) with **typed ERD** (architect)—flag **gaps**, do not pretend they match without checking attribute types.
- Auto-incrementing **`NNN`** on **edit** passes of PRD/plan/task—validation does not re-sequence those files.

## Path conventions (this repository)

| Artifact | Pattern |
|----------|---------|
| PRD | `LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md` |
| Plan | `ai-specs/plan/<NNN>-plan.md` |
| Task | `ai-specs/tasks/<NNN>-task.md` |
| Review log (optional) | `ai-specs/review/<NNN>-review.md` |
| User stories backlog | `LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md` |
| Contributor folder | `LTI-<CONTRIBUTOR-SLUG>/` — main doc **`LTI-<CONTRIBUTOR-SLUG>.md`**, **`prompts.md`**, **`ADR.md`**, **`UserStories-<CONTRIBUTOR-SLUG>.md`** |

**`<NNN>`:** `001`–`999`, zero-padded; **next** = max existing match for that directory’s pattern + 1, or `001` if none.
