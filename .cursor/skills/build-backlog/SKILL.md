---
name: build-backlog
description: >-
  Agile Product Owner toolkit: INVEST-compliant user story generation from PRD
  or requirements, acceptance criteria (Given/When/Then), story-point estimation,
  backlog prioritization, and sprint capacity planning. Use when transforming
  requirements into an actionable, sprint-ready backlog—not for PRD authorship
  (generate-prd) or system design (develop-architect). Pair with
  validate-artifacts for cross-doc coherence.
---

# Build Backlog (Agile Product Owner)

## Purpose

Transform **documented requirements** (PRD functional requirements, user stories, use cases) into a **prioritized, sprint-ready product backlog** with **INVEST-compliant** user stories, **testable acceptance criteria**, **story-point estimates**, and **sprint capacity plans**.

## When to Use

- The user asks to **build a backlog**, **create user stories**, **plan a sprint**, **prioritize stories**, **estimate effort**, or **break epics into stories**.
- Requirements exist (PRD, functional requirements, use cases) and the next step is **execution planning**.
- The user wants to turn **milestones or phasing** from a PRD into **sprint-level work items**.

## When Not to Use

- **Product strategy, PRD authorship, or MVP scoping** as the primary task → **generate-prd** (product-manager agent).
- **System architecture, typed ERD, C4 diagrams, or ADRs** → **develop-architect** (architect agent).
- **Cross-document audit** only → **validate-artifacts** (documentation-auditor agent).
- **Git commits** only → **commit**.

## Inputs

- **Requirements source:** **`LTI-<CONTRIBUTOR-SLUG>/<NNN>-prd.md`**, **`LTI-<CONTRIBUTOR-SLUG>/LTI-<CONTRIBUTOR-SLUG>.md`**, or user-provided scope.
- **Contributor slug** for path resolution (default **`LTI-ICS`** in this workspace).
- Optional: existing backlog at **`LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md`** (e.g. `LTI-ICS/UserStories-ICS.md`).
- Optional: team capacity (number of developers, sprint length, velocity baseline).

## Outputs

| Output | Path pattern |
|--------|-------------|
| **User stories backlog** (consolidated: all stories, acceptance criteria, estimates, sprint plans, prioritization) | **`LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md`** (example: **`LTI-ICS/UserStories-ICS.md`**) |
| Git commits | Per **commit** skill |

**Path resolution:** use the active contributor slug (default **`ICS`** in this workspace). The file lives inside the contributor folder alongside the PRD and main deliverable. Create the file if missing; **update in place** on subsequent runs.

## Process

### 1. Gather requirements

Read the PRD or requirements source. Identify:

- **Functional requirements** (FR-NNN) and their priority/phase.
- **User stories** (US-NNN) with acceptance criteria.
- **Use cases** (UC-N) and user journeys.
- **Milestones / phasing** (which FRs map to which phase).
- **Non-functional requirements** that constrain story scope (performance, security, compliance).

### 2. Break epics into INVEST-compliant stories

For each epic or functional area, generate stories that satisfy **INVEST**:

| Criterion | Meaning | Validation |
|-----------|---------|------------|
| **I**ndependent | Minimizes coupling to other stories | Can be developed and deployed without waiting on another story in the same sprint |
| **N**egotiable | Not a rigid contract; details emerge in refinement | Story text describes *what* and *why*, not *how* |
| **V**aluable | Delivers user or business value | Acceptance criteria tie to a persona goal or FR |
| **E**stimable | Team can size it with reasonable confidence | Story is decomposed enough that unknowns are explicit |
| **S**mall | Fits within one sprint | If too large, split by workflow step, persona, or data slice |
| **T**estable | Clear pass/fail criteria | Given/When/Then or equivalent; no vague "works correctly" |

### 3. Write acceptance criteria (BDD)

Each story MUST have acceptance criteria written in **Behavior-Driven Development (BDD)** format using **Given / When / Then**:

```markdown
**Acceptance criteria (BDD):**

- **Given** <precondition>, **when** <action>, **then** <expected outcome>.
- **Given** <alternate precondition>, **when** <action>, **then** <alternate outcome>.
```

Acceptance criteria MUST be:
- **Specific:** include measurable thresholds where relevant (e.g. "maximum 500ms", "at least 3 characters").
- **Exhaustive:** cover the happy path, edge cases, and error/empty states.
- **Testable:** each criterion produces an unambiguous pass/fail result.

Map each criterion to at least one **FR-NNN** or **NFR-NNN** from the PRD where traceability is feasible.

### 4. Estimate story points

Use a **relative sizing** approach (Fibonacci: 1, 2, 3, 5, 8, 13, 21):

| Points | Complexity signal |
|--------|------------------|
| **1–2** | Well-understood, small scope, minimal unknowns |
| **3–5** | Moderate complexity, some integration or design work |
| **8** | Significant effort, multiple components, or unknowns |
| **13** | Large; consider splitting |
| **21** | Epic-sized; MUST split before sprint planning |

State assumptions behind estimates (team familiarity, tech stack, dependencies).

### 5. Prioritize the backlog

The backlog MUST be **sorted by priority** (highest first). Apply a **multi-factor** prioritization using **all seven** factors below. Each story should have a brief justification referencing the dominant factors that determined its position.

| # | Factor | What to evaluate |
|---|--------|-----------------|
| 1 | **Business Value** | User stories and enhancements that deliver the greatest value to business or end users: impact on user retention, appeal to new users, revenue potential. |
| 2 | **Urgency** | Features most urgent in terms of market needs or stakeholder commitments. |
| 3 | **Dependencies** | Tasks that other tasks depend on for implementation — prioritize to ensure a logical and efficient workflow. |
| 4 | **Implementation Cost** | Effort, resources, and time required. Prioritize those with the best cost-benefit ratio. |
| 5 | **Potential Risks and Obstacles** | Risks associated with each story and their potential impact on the project. High-risk items may need early attention for risk reduction. |
| 6 | **User Feedback** | User opinions and preferences, especially in critical areas of the UI/UX. |
| 7 | **Technological Maturity** | Maturity and feasibility of the proposed technological solutions for each task. |

Assign a priority label to each story:

| Method | Labels |
|--------|--------|
| **MoSCoW** | Must / Should / Could / Won't (this sprint) |
| **P-level** | P0 (critical) / P1 (high) / P2 (medium) / P3 (low) |

The **Backlog overview** table MUST be sorted by priority (P0 first, then P1, etc.). Within the same priority level, sort by dependencies (blockers first) then by business value.

### 6. Plan sprints with capacity

When the user provides (or the PRD implies) team composition and timeline:

1. **Sprint length:** default 2 weeks unless user specifies otherwise.
2. **Team velocity:** if unknown, estimate conservatively (e.g. 70% of raw capacity for a new team).
3. **Capacity per sprint:** `team_size × available_days × focus_factor × avg_points_per_day`.
4. **Allocation:** fill sprints respecting priority order, dependencies, and phase boundaries.
5. **Buffer:** reserve ~15–20% capacity for unknowns and technical debt.

### 7. Write the output file

All output goes into a **single consolidated file**: **`LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md`** (example: **`LTI-ICS/UserStories-ICS.md`**).

**File template:**

```markdown
# User Stories — LTI ATS

## Document control
- **Version:** 0.1
- **Last updated:** <YYYY-MM-DD>
- **Source:** <PRD path or user-provided scope>

## Backlog overview

<!-- MUST be sorted by priority: P0 first, then P1, P2, P3. Within same priority: dependencies first, then business value. -->

| ID | User story | Points | Priority | Sprint | FR traceability |
|----|-----------|--------|----------|--------|-----------------|
| S-001 | As a **recruiter**, I want to … so that … | 5 | P0 | Sprint 1 | FR-001, FR-003 |

## Sprint plan

### Sprint 1 — <sprint goal>

| Parameter | Value |
|-----------|-------|
| Sprint length | <N> weeks |
| Team size | <N> developers |
| Estimated velocity | <N> story points |
| Buffer | <N>% |

#### Stories

| ID | Story | Points | Priority | FR traceability | Status |
|----|-------|--------|----------|-----------------|--------|
| S-001 | … | 5 | P0 | FR-001, FR-003 | To Do |

#### Dependencies and risks
<!-- Cross-story dependencies, external blockers, unknowns -->

### Sprint 2 — <sprint goal>
<!-- Same structure as Sprint 1 -->

## Story details

<!-- Stories MUST appear in priority order (same as Backlog overview). -->

### S-001 — <Story title>

**User story:**

As a **<persona>**,

I want to **<action>**,

so that **<benefit>**.

**Story points:** <N>  
**Priority:** <P-level or MoSCoW>  
**Priority justification:** <!-- 1–2 sentences citing dominant factors: Business Value, Urgency, Dependencies, Implementation Cost, Risks, User Feedback, Technological Maturity -->

**Acceptance criteria (BDD):**

- **Given** <precondition>, **when** <action>, **then** <expected outcome>.
- **Given** <alternate precondition>, **when** <action>, **then** <alternate outcome>.
- **Given** <error/edge-case precondition>, **when** <action>, **then** <fallback outcome>.

**Additional notes:**

- <!-- Implementation considerations, integration requirements, accessibility, performance thresholds -->
- <!-- Technical constraints or recommendations -->

**Related user stories:**

- S-NNN: <related story title>

**FR traceability:** FR-001, FR-003

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-002 — <Story title>
<!-- Same structure as S-001 -->

## Assumptions and open questions
<!-- Capacity assumptions, tech stack familiarity, unknowns -->

## Definition of Done
<!-- Sprint-level DoD: code reviewed, tests pass, acceptance criteria met, docs updated -->
```

## Velocity tracking

When the user provides actuals (completed points per sprint), compute:

- **Velocity:** average completed story points over last 3 sprints.
- **Predictability:** standard deviation of velocity (lower = more predictable).
- **Burndown trend:** on track / ahead / behind based on remaining scope vs remaining sprints.

Present as a summary table or Mermaid chart when useful.

## Quality Checks

| Check | Pass |
|-------|------|
| **INVEST** | Every story satisfies all six criteria or has an explicit exception noted |
| **BDD acceptance criteria** | Every story has at least two Given/When/Then scenarios covering happy path and edge/error case |
| **Epic decomposition** | No story > 13 points; epics are split by workflow step, persona, or data slice — not by technical layer |
| **Traceability** | Stories map to FR-NNN or use-case references from the PRD |
| **Estimates** | Fibonacci story points assigned with stated assumptions |
| **Priority** | Every story has an explicit priority label with justification citing the 7 prioritization factors |
| **Sort order** | Backlog overview and story details are sorted by priority (P0 first) |
| **Related stories** | Cross-references between dependent or related stories are present |
| **Additional notes** | Implementation considerations, accessibility, performance thresholds noted where relevant |
| **Sprint capacity** | Total points per sprint ≤ estimated velocity (with buffer) |
| **Phase alignment** | Sprint stories respect PRD milestone boundaries |
| **Naming** | Output file is **`LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md`** inside the contributor folder |

**Bad output:** Stories without BDD acceptance criteria; vague "implement feature X" items; no priority or estimate; unsorted backlog; stories > 13 points not split; sprint overloaded beyond capacity; stories that duplicate or contradict PRD scope; missing related stories cross-references.

**Good output:** INVEST-validated stories with BDD Given/When/Then (happy + edge cases), Fibonacci estimates with assumptions, multi-factor priority justification, FR traceability, related story links, additional notes, and sprint plans that respect capacity and phase boundaries — all in one consolidated `UserStories-<CONTRIBUTOR-SLUG>.md` file sorted by priority.

## Create vs Update Guidance

| Situation | Action |
|-----------|--------|
| **New** backlog (file does not exist) | Create **`LTI-<CONTRIBUTOR-SLUG>/UserStories-<CONTRIBUTOR-SLUG>.md`** using the template above |
| **Update** existing backlog | **Read** the file first; merge new stories, update estimates/priorities, add sprints; bump **Document control / Version** |
| **Re-prioritize** backlog | Update priorities and sprint assignments in place; note what changed and why in the commit message |
| **Add stories from new PRD phase** | Append new stories to the backlog overview and story details sections; assign to new or existing sprints |

**Overwrite rule:** Never replace the entire file without reading and merging unless the user explicitly asks to **replace**.

## Common Mistakes to Avoid

- Writing stories as **implementation tasks** ("create database table") instead of **user-valuable outcomes**.
- Skipping acceptance criteria or writing vague ones ("works as expected").
- Overloading sprints beyond velocity—always respect capacity with buffer.
- Ignoring PRD phase boundaries when sequencing stories.
- Estimating without stating assumptions about team skill and tech stack.
- Creating stories that expand scope beyond documented PRD requirements without labeling as **assumption** or **Open question**.

## Relationship to Other Skills

| Skill | Relationship |
|-------|-------------|
| **generate-prd** | Upstream: PRD provides the requirements this skill transforms into stories |
| **develop-architect** | Parallel: technical design informs story complexity and dependencies |
| **validate-artifacts** | Downstream: validates coherence between backlog and PRD/architecture |
| **commit** | After: persist backlog artifacts to git |

The **product-owner** agent is the intended **primary owner** of this `SKILL.md`.
