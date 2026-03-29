---
name: commit
description: >-
  Creates git commits using a fixed conventional message shape. Use when the
  user asks to commit, stage work, or snapshot changes—not for rewriting
  document content. Does not run validation; pair with validate-artifacts if
  needed before push.
---

# Commit

## Purpose

Record a **scoped, traceable** git snapshot with a **single-line conventional subject** so history stays readable in a multi-contributor design repo.

## When to Use

- The user asks to **commit**, **save to git**, **stage**, or **snapshot** changes.
- Finishing a task where **version control** is expected (docs, skills, rules, deliverables).

## When Not to Use

- There are **no staged/uncommitted** changes (say so; do not create an empty commit).
- The user asked only to **validate** or **edit** files—commit comes **after** they approve changes.
- **Secrets or accidental binaries** appear in `git status`—stop and report; do not commit.

## Inputs

- Working tree state (`git status`, `git diff` as needed).
- **Explicit** path list from the user for `git add` (avoid blind `git add -A` unless requested).

## Outputs

- One or more **git commits** with subjects matching **Message format** below.
- Optional **multi-line body** (blank line after subject) for breaking changes or non-obvious rationale.

## Process

1. Run **`git status`** (and **`git diff`** / **`git diff --staged`** if needed) so the commit matches reality.
2. Stage **only** intended paths: **`git add <paths>`**.
3. Compose **one subject line**; add **body** only when necessary.
4. Run **`git commit -m "type(scope): Subject"`** (and second **`-m`** for body). Request **`git_write`** permission when executing.

## Message format (required)

Single-line subject (no trailing period):

```text
<type>(<scope>): <Imperative description with capitalized first word after the colon>
```

**Example (canonical for this repo):**

```text
feat(dn): Add new diagram for candidates component
```

- **type:** `feat` | `fix` | `docs` | `chore` | `refactor` | `style` | `test` — closest [Conventional Commits](https://www.conventionalcommits.org/) type.
<type>(<scope>): <Imperative description with capitalized first word after the colon>
**description:** Imperative mood; **first word after `:` is capitalized** to match project examples; **no** trailing period.

### Suggested scopes (LTI design repo)

| scope | Use for |
|-------|--------|
| `dn` | Diagrams (Lean Canvas, use case, C4, HLD, etc.) |
| `doc` | Main deliverable markdown (`LTI-*.md`) narrative/structure |
| `prompts` | `prompts.md` or prompt log |
| `rules` | `.cursor/rules` |
| `skills` | `.cursor/skills` |
| `review` | Validation reports under `ai-specs/review/` |
| `repo` | Root **`ReadMe.md`**, shared repo layout, `.gitignore`, CI |

Unrelated changes → **separate commits**; avoid one vague message covering multiple scopes.

## Quality Checks

| Check | Pass |
|-------|------|
| Subject matches `type(scope): Subject` | Regex-shaped; no trailing `.` |
| Staged files match user intent | Only requested paths |
| No secrets in diff | No keys, tokens, private URLs with credentials |

**Bad output:** Generic message (`update files`), wrong scope, or mixed unrelated changes in one commit.

**Good output:** One clear imperative subject; user told exactly what was committed.

## Create vs Update Guidance

- **Create** a new commit for each approved snapshot; do not **amend** (`--amend`) unless the user explicitly asks to fix the **last** commit message or content.
- **Update** remote history (force push) is **out of scope** unless the user explicitly requests it and understands the risk—default is **no** force push.

## Common Mistakes to Avoid

- **`git add -A`** without confirmation when only part of the tree should ship.
- Committing **`.env`**, API keys, or **large generated artifacts**.
- **Multiple logical changes** in one commit when splitting would make `git blame` useful.

## Examples

See [examples.md](examples.md) for more message samples.
