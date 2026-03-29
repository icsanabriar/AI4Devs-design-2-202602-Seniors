# Cursor setup — operational guide

This folder configures **Cursor** for the LTI / AI4Devs design exercise: **agents** (specialized subagents), **skills** (repeatable procedures), and **rules** (governance). The goal is consistent, auditable documentation—not application code.

**Independence from root docs:** Repository-root **`ReadMe.md`** (course brief) is **not** part of `.cursor/` and **must not** be required to link here. Governance for assistants using this setup is defined under **`.cursor/rules/`** and this file.

## Path patterns: what is real vs example

| Kind | Meaning for a new contributor |
|------|------------------------------|
| **Real paths under `.cursor/`** | Files and folders **committed in this repo**—listed in [Files on disk](#files-on-disk-authoritative-active-layout) below. These exist after clone (for this branch). |
| **Repository root** | **`ReadMe.md`** is the **course brief** (real file name, capital **M**). It is **not** inside `.cursor/`. |
| **Contributor tree (pattern)** | **`LTI-<CONTRIBUTOR-SLUG>/`** is a **folder you create** (example: **`LTI-ICS/`** when `<CONTRIBUTOR-SLUG>` is `ICS`). Required course files inside it are defined in **`.cursor/rules/10-project-overview.mdc`** and **`40-naming-and-paths.mdc`**. |
| **`ai-specs/` (pattern)** | **`ai-specs/plan/`**, **`ai-specs/tasks/`**, **`ai-specs/review/`** are **conventions for optional generated artifacts**. The **`ai-specs/`** directory may **not exist** until someone creates the first file—treat paths as **templates**, not as proof the folder is already on disk. |
| **Angle-bracket tokens** | **`<CONTRIBUTOR-SLUG>`**, **`<NNN>`**, etc. are **placeholders**—replace them; do not create filenames that still contain `<` or `>`. Full definitions: [Placeholder lexicon](#placeholder-lexicon-paths-in-docs). |

## Repository map

| Path | Contents |
|------|----------|
| [`.cursor/agents/`](agents/) | Agent definitions: `architect.md`, `product-manager.md`, `product-owner.md`, `documentation-auditor.md` |
| [`.cursor/skills/`](skills/) | One `SKILL.md` per skill (subfolders: `build-backlog`, `commit`, `develop-architect`, `generate-prd`, `validate-artifacts`) plus [`commit/examples.md`](skills/commit/examples.md) |
| [`.cursor/rules/`](rules/) | Numbered `.mdc` rules (`10-` … `60-`), some `alwaysApply`, some scoped by glob |

### Files on disk: authoritative active layout

Paths below are **real `.cursor/` paths** in this repository (relative to **`.cursor/`**). They are the **intended active** agents, rules, and skills.

**Legacy / non-default:** If **`skills/plan-story/`** or **`skills/improve-story/`** appear in a clone, they are **not** part of the default operating model—omit them from this table and from workflow expectations unless your team explicitly re-enables them.

| Path |
|------|
| `README.md` (this guide) |
| `agents/architect.md` |
| `agents/product-manager.md` |
| `agents/product-owner.md` |
| `agents/documentation-auditor.md` |
| `rules/10-project-overview.mdc` |
| `rules/20-deliverable-markdown.mdc` |
| `rules/30-prompt-tracking.mdc` |
| `rules/40-naming-and-paths.mdc` |
| `rules/50-diagram-standards.mdc` |
| `rules/60-review-and-validation.mdc` |
| `skills/build-backlog/SKILL.md` |
| `skills/commit/SKILL.md` |
| `skills/commit/examples.md` |
| `skills/develop-architect/SKILL.md` |
| `skills/generate-prd/SKILL.md` |
| `skills/validate-artifacts/SKILL.md` |

**Active skills (default workflow):** **`build-backlog`**, **`commit`**, **`develop-architect`**, **`generate-prd`**, **`validate-artifacts`**—see [Skills inventory](#skills-inventory). **Verify** with [Setup health check](#setup-health-check-cursor-tooling).

### Placeholder lexicon (paths in docs)

| Token | Meaning |
|-------|---------|
| **`<CONTRIBUTOR-SLUG>`** | Contributor folder suffix: root is **`LTI-<CONTRIBUTOR-SLUG>/`** (example: `ICS` → `LTI-ICS/`). |
| **`<NNN>`** | Three-digit zero-padded index **`001`–`999`** for one numbered series **per target directory** (e.g. PRDs in **`LTI-<CONTRIBUTOR-SLUG>/`**; optional plans in **`ai-specs/plan/`**, tasks in **`ai-specs/tasks/`**, reviews in **`ai-specs/review/`**) per **`.cursor/rules/40-naming-and-paths.mdc`**. |
| **`LTI-ICS`** (in examples) | Concrete example slug only—not a second placeholder pattern. |

Do **not** use malformed stems such as bare **`-prd.md`** or **`LTI-/LTI-.md`**; always show **`LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md`** or **`LTI-<CONTRIBUTOR-SLUG>/LTI-<CONTRIBUTOR-SLUG>.md`**.

### Authoritative rules (single stack)

**`.cursor/rules/`** contains **only** these six files—**no** parallel unnumbered legacy rules (e.g. `project-overview.mdc` without the `10-` prefix):

| File |
|------|
| `10-project-overview.mdc` |
| `20-deliverable-markdown.mdc` |
| `30-prompt-tracking.mdc` |
| `40-naming-and-paths.mdc` |
| `50-diagram-standards.mdc` |
| `60-review-and-validation.mdc` |

If you extend governance, add a **new numbered** file and update **`.cursor/rules/10-project-overview.mdc`** (stack table) and this README—**do not** duplicate the same policy under two filenames.

## Architecture: how the pieces fit

```text
Rules (10–60)     →  MUST / MUST NOT governance; always win on conflict
       ↓
Agents            →  Role boundaries, handoffs, which skills to read first
       ↓
Skills            →  Concrete paths, templates, create/update vs validate
       ↓
Artifacts         →  Required: LTI-<CONTRIBUTOR-SLUG>/*.md (deliverable, prompts, ADR, optional PRD)
                    Optional: ai-specs/plan|tasks|review/<NNN>-*.md when created
```

- **Rules** apply to any assistant turn when in scope (`alwaysApply` or matching glob). They define course layout, prompt logging, paths, diagrams, validation expectations.
- **Agents** narrow *who does what* and *when to hand off*; they point to skills and numbered rules.
- **Skills** encode *how* to name files, fill templates, validate, or commit—without replacing agent ownership.

## Collaboration model

- **Humans** own the contributor folder (e.g. `LTI-ICS/`) and PRs.
- **Product-oriented** edits → **`/product-manager`** (skill: **`generate-prd`**).
- **Backlog and sprint planning** → **`/product-owner`** (skill: **`build-backlog`**). Output: **`LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md`** (e.g. `LTI-ICS/UserStories-ICS.md`).
- **Technical design** → **`/architect`** + **`develop-architect`** (diagrams, typed ERD, ADRs).
- **Review before submit** → **`/documentation-auditor`** + **`validate-artifacts`** skill (structured report).
- **Never** use an agent to silently override another role’s ownership—use **handoffs** (see agent files).

## Rule precedence

Rules are ordered **`10-`** (foundation) through **`60-`** (validation governance). See **`.cursor/rules/10-project-overview.mdc`** for the stack table.

- **Narrower scope wins** for its topic (e.g. **`.cursor/rules/20-deliverable-markdown.mdc`** on `LTI-*/LTI-*.md` for main deliverable sections).
- On conflict: **follow the rule**, not ad-hoc agent habits.
- **`alwaysApply: true`:** `10-`, `30-`, `40-`, `60-`. **`alwaysApply: false` (glob-scoped):** `20-` (`**/LTI-*/LTI-*.md`), `50-` (`LTI-*` + `ai-specs/**/*.md`).

---

## Agents

Invoke via Cursor’s agent picker (e.g. **`/architect`**, **`/product-manager`**, **`/product-owner`**, **`/documentation-auditor`**—exact UX depends on Cursor version).

### `architect`

| | |
|--|--|
| **Mission** | Turn agreed goals into coherent **technical** design: C4-aligned Mermaid, typed data models, NFRs, ADRs. |
| **When to use** | HLD, containers, deep C4 on one component, `erDiagram`, ADR updates, technical plans/tasks. |
| **When not to use** | Replacing product strategy, MVP calls, or PRD intent without PM alignment. |
| **Owns** | Technical structure, diagrams (with **`.cursor/rules/50-diagram-standards.mdc`**), **`LTI-<CONTRIBUTOR-SLUG>/ADR.md`** when logging decisions. |
| **Does not own** | Lean Canvas, positioning, final prioritization. |
| **Handoffs** | To **`/product-manager`** for ambiguous requirements or prioritization; expects PRD/deliverable product sections for glossary alignment. |

### `product-manager`

| | |
|--|--|
| **Mission** | ATS-aware product narrative: pains, differentiation, PRD shape, use-case stories, MVP phasing themes. |
| **When to use** | PRD, goals, functions, Lean Canvas, use-case narratives, MoSCoW/themes. |
| **When not to use** | Final typed ERD, authoritative C4 depth, infrastructure truth—use **`/architect`**. |
| **Owns** | Product language, `generate-prd` output, leading product sections in `LTI-*.md`. |
| **Does not own** | ADRs, final architecture diagrams as engineering record. |
| **Handoffs** | To **`/architect`** for boundaries, typed models, sequence diagrams with stores/auth, deployment concerns. |

### `product-owner`

| | |
|--|--|
| **Mission** | Bridge product strategy and engineering execution: transform PRD requirements into a **prioritized, sprint-ready backlog** with INVEST-compliant stories, acceptance criteria, estimates, and sprint plans. |
| **When to use** | Building a backlog, creating/refining user stories, sprint planning, estimating effort, prioritizing work, velocity tracking. |
| **When not to use** | PRD authorship or product strategy (use **`/product-manager`**); system architecture, C4, ERDs, ADRs (use **`/architect`**). |
| **Owns** | `build-backlog` skill output: **`LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md`** (consolidated backlog with stories, estimates, sprint plans), INVEST validation, capacity planning. |
| **Does not own** | PRD files, Lean Canvas, product positioning, system architecture, ADRs. |
| **Handoffs** | To **`/product-manager`** for ambiguous requirements, scope changes, or prioritization calls; to **`/architect`** for technical feasibility, dependencies, or spike definitions. |

### `documentation-auditor`

| | |
|--|--|
| **Mission** | **Audit** docs: completeness, consistency, traceability, rule compliance—not ghostwriting. |
| **When to use** | Pre-submission review, after big merges, when artifacts may contradict each other. |
| **When not to use** | As substitute for PM or architect when the task is to **decide** product or architecture. |
| **Owns** | Findings reports, gap lists, compliance mapping to rules; default workflow uses **`validate-artifacts`** skill. |
| **Does not own** | Product strategy, final architecture, inventing requirements. |
| **Handoffs** | To **`/product-manager`** (ambiguous value/priorities); to **`/architect`** (technical inconsistency, missing ADRs). |

---

## Skills inventory

**Intended active skills** for this repository’s default operating model:

| Skill | Folder | Purpose | Primary agents | Create / update / validate |
|-------|--------|---------|----------------|----------------------------|
| **build-backlog** | [`skills/build-backlog/`](skills/build-backlog/) | INVEST-compliant user stories, acceptance criteria, story-point estimation, backlog prioritization, sprint capacity planning → **`LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md`** | **`/product-owner`** | **Create/update** consolidated backlog file |
| **develop-architect** | [`skills/develop-architect/`](skills/develop-architect/) | Architecture drivers, C4 Mermaid, clean-architecture framing, ADR append rules | **`/architect`** | **Create/update** design text & diagrams |
| **generate-prd** | [`skills/generate-prd/`](skills/generate-prd/) | PRD template → `LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md` (default **`LTI-ICS/`**) | **`/product-manager`** | **Create/update** PRD files |
| **validate-artifacts** | [`skills/validate-artifacts/`](skills/validate-artifacts/) | Cross-doc validation report; optional `ai-specs/review/<NNN>-review.md` | **`/documentation-auditor`** (default), anyone | **Validation-oriented** (read-only on sources unless user asks to apply fixes) |
| **commit** | [`skills/commit/`](skills/commit/) | Conventional commit messages | Any agent after doc changes | **Git snapshot** (not doc authoring) |

**When not to use:** Each skill’s `SKILL.md` has **When Not to Use**—e.g. `validate-artifacts` is not legal/compliance review; `commit` is not for fixing content without user intent.

**Backlog output:** **`/product-owner`** with **`build-backlog`** writes a consolidated backlog to **`LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md`** (e.g. `LTI-ICS/UserStories-ICS.md`). **Optional `ai-specs` plans and tasks** (`ai-specs/plan/<NNN>-plan.md`, `ai-specs/tasks/<NNN>-task.md` per **`.cursor/rules/40-naming-and-paths.mdc`**) remain available for other agents when needed.

---

## Setup health check (Cursor tooling)

Run this when touching **`.cursor/`**, before merge, or during periodic audits. Goal: confirm **internal references and layout** still match this guide—not to validate student **`LTI-*`** content (use **`validate-artifacts`** / **`/documentation-auditor`** for that).

| # | Check | How to verify (examples) | Pass if |
|---|--------|---------------------------|---------|
| 1 | **Rules stack** | List **`.cursor/rules/`** | Exactly **six** files matching **`10-*.mdc`** through **`60-*.mdc`**; filenames align with the stack table in **`.cursor/rules/10-project-overview.mdc`**. |
| 2 | **Agents** | List **`.cursor/agents/`** | **`architect.md`**, **`product-manager.md`**, **`product-owner.md`**, **`documentation-auditor.md`** present; each references **`.cursor/rules/NN-*.mdc`** and **`.cursor/skills/.../SKILL.md`** paths that exist. |
| 3 | **Active skills** | List **`.cursor/skills/`** | Folders **`build-backlog`**, **`commit`**, **`develop-architect`**, **`generate-prd`**, **`validate-artifacts`** each contain **`SKILL.md`**; **`commit/examples.md`** exists. |
| 4 | **README vs tree** | Open [Files on disk](#files-on-disk-authoritative-active-layout) | Every **non-legacy** path in the table exists on disk; no orphaned active skill folder missing from the table. |
| 5 | **Placeholder discipline** | Spot-check **`.cursor/rules/40-naming-and-paths.mdc`** and this README | **`<CONTRIBUTOR-SLUG>`** and **`<NNN>`** used consistently; no bare `-prd.md` or `-plan.md` stems without **`<NNN>-`**. |
| 6 | **Deliverable validation** | Course submission readiness | Still governed by **`.cursor/rules/60-review-and-validation.mdc`** + **`.cursor/skills/validate-artifacts/SKILL.md`**—unchanged; this table does **not** replace that. |

**Quick command hints (repo root):** `ls .cursor/rules`, `ls .cursor/agents`, `ls .cursor/skills` — compare to this document.

---

## Rules overview (precedence order)

| Path | Purpose | Scope / enforcement |
|------|---------|---------------------|
| **`.cursor/rules/10-project-overview.mdc`** | Repo purpose, LTI context, `LTI-*` layout, collaboration | Global + course layout; foundation |
| **`.cursor/rules/20-deliverable-markdown.mdc`** | Required sections in main deliverable **`LTI-*/LTI-*.md`** | Glob: `**/LTI-*/LTI-*.md` (`prompts.md`: **`.cursor/rules/30-prompt-tracking.mdc`**) |
| **`.cursor/rules/30-prompt-tracking.mdc`** | Mandatory append-only `prompts.md` log, format, failure behavior | Typically always-on; path per contributor slug |
| **`.cursor/rules/40-naming-and-paths.mdc`** | `ai-specs/plan/<NNN>-plan.md`, `ai-specs/tasks/<NNN>-task.md`, `ai-specs/review/<NNN>-review.md`; **`LTI-<CONTRIBUTOR-SLUG>/`** files; basename match; forbid bare `-prd.md` stems | Global naming |
| **`.cursor/rules/50-diagram-standards.mdc`** | Mermaid + C4 semantic/visual consistency, grounding in requirements | `LTI-*` + `ai-specs` markdown with diagrams |
| **`.cursor/rules/60-review-and-validation.mdc`** | Validation before “complete”; alignment across artifacts | Governance to run validation passes |

---

## Recommended workflow (day-to-day)

1. **Read context:** **`.cursor/rules/10-project-overview.mdc`** (authoritative for repo purpose, `LTI-*` layout, collaboration), then your contributor folder convention (`LTI-<CONTRIBUTOR-SLUG>/`). Optionally read the instructor course brief at the repository root if present (**`ReadMe.md`**); that is **outside** `.cursor/` and does **not** need to reference this guide.
2. **Pick an agent** matching the task (product vs architecture vs audit)—see [Agents](#agents).
3. **Open the right skill(s)** from the agent definition or this guide; follow **Create vs Update** in each `SKILL.md` so you do not duplicate `NNN` files incorrectly.
4. **Produce or edit artifacts** in the approved paths (**`.cursor/rules/40-naming-and-paths.mdc`**).
5. **Validate:** use **`/documentation-auditor`** or apply **`validate-artifacts`** before claiming submission-ready (**`.cursor/rules/60-review-and-validation.mdc`**).
6. **Prompts:** every answered user message in Cursor workspaces using this rule set should append to **`LTI-<CONTRIBUTOR-SLUG>/prompts.md`** per **`.cursor/rules/30-prompt-tracking.mdc`** (assistant obligation).
7. **Commit** via **`commit`** skill when persisting to git; separate logical changes.
8. **Hand off** if you hit PM- or architect-owned decisions.

---

## Quick start (new contributor)

1. **Start here:** this document → skim [Agents](#agents), [Rules overview](#rules-overview-precedence-order), [Recommended workflow](#recommended-workflow-day-to-day).
2. **Course deliverable:** read **`.cursor/rules/20-deliverable-markdown.mdc`** and create **`LTI-<CONTRIBUTOR-SLUG>/LTI-<CONTRIBUTOR-SLUG>.md`** + **`prompts.md`** per **`.cursor/rules/10-project-overview.mdc`**.
3. **Choose an agent:** product writing → **`/product-manager`**; backlog/sprints/stories → **`/product-owner`**; diagrams/ERD/C4/ADR → **`/architect`**; pre-submit check → **`/documentation-auditor`**.
4. **Avoid breaking conventions:** never use repository-root `prompts.md` for course prompts; use **`LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md`** not bare `-prd.md`.
5. **Before editing:** open the target **`SKILL.md`** for numbering rules; open **`.cursor/rules/40-naming-and-paths.mdc`** if unsure where a file belongs.

---

## Troubleshooting / common mistakes

| Mistake | Why it hurts | Fix |
|---------|----------------|-----|
| Wrong agent for the job | Scope creep, contradictions | Switch agent; use handoffs |
| Skipping validation | “Looks done” but inconsistent docs | Run **`validate-artifacts`** / **`/documentation-auditor`** |
| Ignoring rule precedence | Silent conflict with course requirements | Cite **`.cursor/rules/NN-*.mdc`**; follow it |
| Wrong paths | Broken links, grader confusion | Use **`.cursor/rules/40-naming-and-paths.mdc`** patterns |
| New `NNN` on **edit** | Duplicate plans/tasks | **Update in place** per **`.cursor/rules/40-naming-and-paths.mdc`** |
| Forgetting prompt log | Fails course / audit trail | **`.cursor/rules/30-prompt-tracking.mdc`** |
| Inconsistent diagram names | Traceability breaks | **`.cursor/rules/50-diagram-standards.mdc`** + one glossary |
| Architect rewrites PRD intent | PM ownership violated | Hand off to **`/product-manager`** |

---

## Operability & maintenance checklist

Use when reviewing a PR or periodically auditing the repo tooling.

- [ ] **`.cursor/rules/`** contains **only** the six numbered `10-`–`60-` `.mdc` files (no unnumbered legacy duplicates).
- [ ] All **`.cursor/agents/*.md`** references to rules use **`.cursor/rules/NN-*.mdc`** paths—no stale unnumbered filenames.
- [ ] Each **agent** points to **real** skill paths under **`.cursor/skills/`**.
- [ ] **Path conventions** in rules, skills, and docs agree (`<NNN>` three-digit, `LTI-<CONTRIBUTOR-SLUG>/`).
- [ ] **`documentation-auditor`** still defaults to **`validate-artifacts`** for full audits (see agent file).
- [ ] **`.cursor/README.md`** [Files on disk](#files-on-disk-authoritative-active-layout) matches the **intended active** tree (including **`skills/commit/examples.md`**); run [Setup health check](#setup-health-check-cursor-tooling) on `.cursor/` PRs.
- [ ] After adding a rule: assign a **new number** in sequence, update this README’s rules table and **`.cursor/rules/10-project-overview.mdc`** stack if needed.
- [ ] After adding an agent: document it here under [Agents](#agents).

---

## Examples (short)

**Create a PRD**  
→ Agent: **`/product-manager`**. Skill: **`generate-prd`**. Output: **`LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md`** (default **`LTI-ICS/`**). Then lift sections into **`LTI-<CONTRIBUTOR-SLUG>/LTI-<CONTRIBUTOR-SLUG>.md`** if that’s your single deliverable.

**Build a sprint backlog from PRD**  
→ Agent: **`/product-owner`**. Skill: **`build-backlog`**. Output: **`LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md`** (e.g. `LTI-ICS/UserStories-ICS.md`).

**Develop architecture (HLD, ERD, C4, ADRs)**  
→ Agent: **`/architect`**. Skill: **`develop-architect`**. Rules: **`.cursor/rules/50-diagram-standards.mdc`**, **`.cursor/rules/20-deliverable-markdown.mdc`** for course sections. ADRs: **`LTI-<CONTRIBUTOR-SLUG>/ADR.md`**.

**Audit before submission**  
→ Agent: **`/documentation-auditor`**. Skill: **`validate-artifacts`** (read first; emit full **Validation report**). Optional save: `ai-specs/review/<NNN>-review.md`.

---

## Extending this setup safely

1. **Rules first** if behavior must be **mandatory** for all assistants in scope.
2. **Skills** for repeatable **file/process** patterns (templates, numbering, validation steps).
3. **Agents** for **role boundaries** and handoffs—keep them thin; link to skills and numbered rules.
4. Update **this README** and **`.cursor/rules/10-project-overview.mdc`** when the stack changes.
5. Run the [Operability checklist](#operability--maintenance-checklist) and [Setup health check](#setup-health-check-cursor-tooling) after changes.

---

## Related documentation

- **Course brief (repo root):** **`ReadMe.md`** in this repository; not maintained under `.cursor/`. **No** requirement that it link to this guide.
- **Contributor prompt log:** `LTI-<CONTRIBUTOR-SLUG>/prompts.md` (per **`.cursor/rules/30-prompt-tracking.mdc`**)
