# ContextForge Skills

A repository-first engineering workflow for AI coding agents.

ContextForge helps teams and solo developers keep **project context, technical decisions, implementation contracts, and proof of correctness in the repository** instead of depending on chat history.

> Core rule: **Decisions and evidence live in the repo. Chat is temporary; the repository is durable.**

## Why ContextForge exists

AI coding agents are fast, but they can make plausible decisions that are wrong for a specific project when the project context is incomplete. ContextForge separates software work into focused skills and gives each skill a durable artifact to read or write.

The result is a workflow that can survive:

- a new Codex or agent session,
- a cleared chat,
- a different model,
- a handoff to another developer,
- a feature that takes several days,
- a bug that appears long after the original implementation.

## Workflow

```text
Idea
  ↓
$scope
  ↓
$decide        ← only when a load-bearing decision is missing
  ↓
$spec
  ↓
$build
  ↓
$verify
  ↓
$test
  ↓
$review
  ↓
$document
  ↓
$sync
```

Use `$debug` whenever something is broken.
Use `$bootstrap` when adopting ContextForge in an existing repository or after initial project scaffolding.

## Skills

| Skill | Responsibility | Durable output |
| --- | --- | --- |
| `bootstrap` | Inspect the real repository and establish durable project context | `AGENTS.md`, `PROJECT_CONTEXT.md` |
| `scope` | Define product boundaries, milestones, and next work | `docs/scope/ROADMAP.md` |
| `decide` | Resolve a load-bearing technical or product decision | `docs/decisions/ADR-*.md` |
| `spec` | Turn an approved change into an implementation contract | `docs/specs/*.md` |
| `build` | Implement the approved spec without inventing missing architecture | source code |
| `verify` | Run the real system and prove acceptance criteria | `docs/evidence/*.md` |
| `test` | Add automated regression coverage | project test files + evidence update |
| `review` | Perform an independent code and architecture review | `docs/reviews/*.md` |
| `debug` | Find root cause, fix the bug, and require regression coverage | code + evidence + test handoff |
| `document` | Write human-facing change documentation from the actual diff | changelog / release / PR text |
| `sync` | Reconcile repository knowledge with what is actually implemented | updated context, scope, specs, ADR status |

## Workflow depth

ContextForge supports three practical depths:

### Quick

```text
$build → $verify → $sync
```

Use for low-risk, obvious, reversible changes. The decision gate still applies.

### Standard

```text
$spec → $build → $verify → $test → $sync
```

Use for normal product work.

### Strict

```text
$decide → $spec → $build → $verify → $test → $review → $document → $sync
```

Use for risky, cross-cutting, security-sensitive, data-model, infrastructure, or release-critical work.

## The two ledgers

ContextForge is built around two durable ledgers:

1. **Decision ledger** — `docs/decisions/`
   - Records why a load-bearing choice was made.
   - Prevents future agents from silently replacing it with a generic default.

2. **Evidence ledger** — `docs/evidence/`
   - Records what was actually run and observed.
   - Prevents "looks correct" from being treated as "verified correct."

## Install from GitHub

After publishing this repository under your GitHub account:

```bash
npx skills@latest add Jack-webcoder/contextforge-skills
```

To target a specific supported agent:

```bash
npx skills@latest add Jack-webcoder/contextforge-skills -a codex
```

List the skills available in the repository:

```bash
npx skills@latest add Jack-webcoder/contextforge-skills--list
```

## Local development

You can test the repository locally before publishing:

```bash
npx skills@latest add ./contextforge-skills
```

Then restart or reopen your coding agent if the newly installed skills are not visible.

## Recommended project artifacts

A project using ContextForge typically contains:

```text
AGENTS.md
PROJECT_CONTEXT.md

docs/
├── scope/
│   └── ROADMAP.md
├── decisions/
│   └── ADR-0001-example.md
├── specs/
│   └── feature-example.md
├── evidence/
│   └── feature-example.md
├── reviews/
│   └── feature-example.md
└── releases/
```

## Greenfield project

```text
$scope
→ $decide   (choose stack / architecture)
→ scaffold the real project
→ $bootstrap
→ $spec
→ $build
→ $verify
→ $test
→ $sync
```

## Existing project

```text
$bootstrap
→ $scope
→ $decide   (only when a missing decision blocks work)
→ $spec
→ $build
→ $verify
→ $test
→ $sync
```

## Design principles

- One skill, one primary responsibility.
- Durable project truth belongs in files.
- Agents may propose decisions, but must not silently make load-bearing decisions.
- Acceptance criteria are the contract between planning and implementation.
- Verification must record commands and observed outcomes.
- Tests protect behavior; verification proves the actual changed system was exercised.
- Sync is reconciliation, not storytelling: repository files must match reality.
- Prefer the smallest workflow that safely fits the change.

## License

MIT. See [LICENSE](LICENSE).
