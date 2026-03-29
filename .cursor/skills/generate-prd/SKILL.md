---
name: generate-prd
description: >-
  Produces a structured PRD for an ATS from a short brief, default path
  LTI-ICS/<NNN>-prd.md (same pattern under other LTI-<SLUG>/ folders). Use for
  product specs and LTI/ATS scope—not for typed ERDs or deep C4
  (develop-architect). Pair with validate-artifacts before handoff when multiple
  docs must align.
---

# Generate PRD (ATS)

## Purpose

Expand a **short ATS-oriented description** into a **structured PRD** (Markdown) with **testable FRs**, **NFRs**, explicit **Open questions**, and optional **Mermaid** for course-aligned sections.

## When to Use

- The user asks for a **PRD**, **product spec**, **requirements doc**, **roadmap inputs**, or **LTI/ATS scope** from a brief.

## When Not to Use

- **Final typed ERD** (attributes + engineering types) or **deep C4** as the authoritative design → **develop-architect** (and architect agent).
- **Execution plan** only as the primary artifact → use **`ai-specs/plan/<NNN>-plan.md`** per **`.cursor/rules/40-naming-and-paths.mdc`** (this skill does not own that template).
- **Single story** refinement as the primary artifact → use **`ai-specs/tasks/<NNN>-task.md`** per **`.cursor/rules/40-naming-and-paths.mdc`** (this skill does not own that template).
- **Cross-document audit** → **validate-artifacts**.

## Inputs

- **General description**: vision, problem, audience, bullets.
- Optional: **existing PRD path** to update (see **Create vs Update**).
- Optional: **alternate output path** if user names one explicitly (then **skip** default `NNN` sequencing for that run).

## Outputs

- **Default file path (this workspace example slug):**

```text
LTI-ICS/<NNN>-prd.md
```

- **Other contributors:** same pattern under their folder — **`LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md`** per **`.cursor/rules/40-naming-and-paths.mdc`** (e.g. **`LTI-ARM/001-prd.md`**).
- **`<NNN>`** — three-digit zero-padded (`001`, `002`, …). Scan the **target contributor folder** (default **`LTI-ICS/`**) for **`^\d{3}-prd\.md$`**, use **max + 1**, or **`001`** if missing/empty. Create the folder if needed.
- If the user **names a different path**, write there and **document** that choice in the reply (no automatic `NNN`).

**Forbidden ambiguous form:** path ending in only `-prd.md` without a numeric prefix.

## Process

1. Parse the description; **one** clarifying question only if **blocking**; otherwise use **Open questions** in the PRD.
2. Resolve **create vs update** target path (below).
3. Fill **PRD template**; add **Lean Canvas**, **Use cases** (three), and course-oriented sections when supporting repository-root **`ReadMe.md`** and the active **`LTI-<CONTRIBUTOR-SLUG>/`** deliverable tree.
4. Reply with **exact path** and a **one-paragraph** scope summary.

## PRD template (required sections)

Use this outline; adapt depth to input size.

**Course-aligned PRDs** (supporting **`LTI-*`** / AI4Devs deliverables): **`## Lean Canvas`** and **`## Use cases`** (exactly **three** primary use cases, each with narrative **and** a **Mermaid** diagram) are **mandatory** in this template so outputs stay course-shaped. When **validate-artifacts** reviews a PRD, treat **completeness** as **section presence**—including those headings and the substructure this template calls for—not as automated proof that every diagram is substantive or non-placeholder. **Diagram quality**, placeholder Mermaid, and how fully the third use case is developed are normally judged by **manual audit** or **downstream** review (for example when work is consolidated into **`LTI-<CONTRIBUTOR-SLUG>/LTI-<CONTRIBUTOR-SLUG>.md`**, where **`.cursor/rules/20-deliverable-markdown.mdc`** applies to the **main deliverable**, not to **`LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md`**). **validate-artifacts** may still **flag** thin content, but it does not replace that deeper pass.

```markdown
# <Product name> — Product Requirements Document

## Document control
- **Version:** 0.1
- **Last updated:** <YYYY-MM-DD>
- **Author / source:** <brief note>

## Executive summary
<!-- Problem, opportunity, and recommended direction in ~5–10 sentences. -->

## Goals and non-goals
### Goals
### Non-goals

## Target users and personas
<!-- Recruiter, hiring manager, candidate (if in-scope), admin — goals and pains. -->

## Problem statement
## Proposed solution (high level)

## User journeys (summary)
<!-- 2–5 bullets per primary journey; link to future use-case docs if needed. -->

## Lean Canvas
<!-- REQUIRED (course-aligned): Business model canvas — Mermaid (e.g. flowchart or structured layout) and/or explicit sub-bullets for Problem, Solution, Unique value, Unfair advantage, Customer segments, Channels, Revenue streams, Cost structure, Key metrics. Must be legible when rendered (e.g. GitHub). -->

## Use cases
<!-- REQUIRED (course-aligned): Exactly THREE primary use cases — not fewer, not more. Each ### below MUST have (1) a short narrative and (2) one fenced Mermaid diagram (sequence, flowchart, or approved equivalent) in the generated file — not “TBD” or omitted. -->

### Use case 1 — <primary title>
<!-- 1–3 sentences: primary actor, goal, success criteria. -->
<!-- REQUIRED: Mermaid diagram in a fenced mermaid block immediately after this subsection. -->

### Use case 2 — <primary title>
<!-- Narrative. -->
<!-- REQUIRED: Mermaid diagram below. -->

### Use case 3 — <primary title>
<!-- Narrative. -->
<!-- REQUIRED: Mermaid diagram below. -->

## Functional requirements
<!-- Numbered FRs: FR-001 … Each testable; mark MoSCoW or Priority P0–P3 if helpful. -->

## Non-functional requirements
<!-- NFR categories: security, privacy, performance, reliability, accessibility, observability. -->

## Success metrics
<!-- Leading/lagging metrics; avoid vanity metrics. -->

## Milestones / phasing
<!-- MVP vs later; dependencies called out. -->

## Risks, assumptions, dependencies

## Open questions
<!-- Explicit gaps; do not fabricate vendor or legal detail. -->

## Appendix
### Glossary
### References
```

## ATS domain lenses (use where relevant)

- **Entities:** requisitions/jobs, candidates/applications, pipeline stages, offers, users/roles (recruiter, hiring manager, admin).  
- **Flows:** sourcing, apply, screen, interview schedule, feedback, decision, hire/reject, compliance/consent.  
- **Collaboration:** real-time or shared visibility between recruiters and hiring managers.  
- **Automations & AI:** scoring, scheduling assistance, drafting, **human-in-the-loop** where decisions affect candidates.  
- **Non-functional:** privacy, retention, audit trails, accessibility, performance, integrations (HRIS, calendar, email).

## Alignment with `ReadMe.md` (LTI / AI4Devs deliverable)

When the PRD supports the **course bundle** (single **`LTI-<CONTRIBUTOR-SLUG>/LTI-<CONTRIBUTOR-SLUG>.md`** — basename matches folder, e.g. **`LTI-ICS/LTI-ICS.md`**), ensure the PRD (or export into that file) can supply:

| Course checklist item | In PRD (this skill) |
|----------------------|---------------------|
| Brief description, value, competitive advantages | **Executive summary**, **Goals**, **Proposed solution** |
| Main functions | **Functional requirements**, **User journeys** |
| Lean Canvas | Section **## Lean Canvas** with **Mermaid** or structured canvas |
| 3 main use cases + diagram each | **## Use cases** — exactly **three** `###` subsections; each: narrative + fenced **`mermaid`** |
| Data model (conceptual) | **## Data model (conceptual)** — entities/relationships; flag **finalize with architect** for typed ERD |
| High-level system design + diagram | **## High-level system design** — prose + Mermaid at product depth |
| C4 depth on one component | **## C4 component focus (draft)** or explicit handoff to **develop-architect** |

**Primary consumer:** **product-manager** agent. PRD lives alongside the deliverable as **`LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md`** (default folder **`LTI-ICS/`**) **and** may be **merged** into **`LTI-<CONTRIBUTOR-SLUG>/LTI-<CONTRIBUTOR-SLUG>.md`** per course rules.

## Quality Checks

| Check | Pass |
|-------|------|
| FRs | Each **FR-NNN** is **testable** (“system shall…” or equivalent clarity) |
| Course bundle | **Lean Canvas** present; **Use cases** has **exactly three** `###` subsections, each with narrative **+** valid fenced **`mermaid`** diagram when PRD is course-aligned |
| Traceability | Goals → FRs → metrics where obvious; glossary for overloaded terms |
| Honesty | No fabricated compliance/vendor claims; gaps in **Open questions** |
| Tone | Product-level; defer **component-level C4** and **typed ERD** depth to **develop-architect** |
| Secrets | Redact tokens, salaries, PII from input |

**Bad output:** Buzzword summary, non-testable FRs, missing **Non-goals** / **Open questions** when scope was underspecified, or course-aligned PRD missing **Lean Canvas** / **three** diagram-backed use cases.

**Good output:** Numbered FRs/NFRs, explicit MVP phasing, Mermaid fences valid, path **`LTI-ICS/<NNN>-prd.md`** (or matching **`LTI-<CONTRIBUTOR-SLUG>/`**) confirmed.

## Create vs Update Guidance

| Situation | Action |
|-----------|--------|
| **New** PRD (default) | Next free `<NNN>` in **`LTI-ICS/`** → create **`LTI-ICS/<NNN>-prd.md`** (or **`LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md`** when the active slug is not `ICS`). |
| **Update** existing **`LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md`** | **Read** file first; **merge** new content into correct sections; bump **Document control / Version**; **preserve FR-NNN** sequence—append new FRs with **next** free numbers, do not renumber existing FRs without user approval. |
| **Merge PRD sections into** `LTI-<CONTRIBUTOR-SLUG>/LTI-<CONTRIBUTOR-SLUG>.md` | **Do not** duplicate **H1**; integrate under existing headings or add clearly labeled sections; note **source PRD path** in a HTML comment or **Document control** if user wants traceability. |
| User gave alternate path | Write there; **do not** auto-assign `NNN` unless user also wants a mirrored copy under the contributor folder. |

**Overwrite rule:** Never replace an entire existing PRD with a fresh template **without** reading and merging unless the user explicitly asks to **replace** the document.

## Common Mistakes to Avoid

- Inventing **legal/regulatory** certainty—in flag as **assumption** or **Open question**.
- Putting **deep C4** or **typed ER** in the PRD as final truth—keep **conceptual** or label **draft pending architect**.
- Leaving **three use cases** at narrative-only when course requires **diagram each**.
- Using ambiguous paths like **`-prd.md`** without **`NNN`**.
