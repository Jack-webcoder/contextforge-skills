# Artifact Contract

This document defines the minimum structure of durable workflow artifacts.

## `AGENTS.md`

Purpose: concise instructions every coding agent should know before working in the repository.

Should contain:

- setup commands,
- build / lint / test commands,
- package manager,
- coding conventions,
- architecture boundaries,
- rules that must always be followed.

Should not become a long project diary.

## `PROJECT_CONTEXT.md`

Purpose: a readable map of the current project.

Should contain:

- product summary,
- stack,
- repository layout,
- main architectural components,
- persistence and external services,
- current constraints,
- links to important ADRs and specs.

## `docs/scope/ROADMAP.md`

Purpose: current product scope and implementation order.

Each roadmap item should have a status:

- `planned`
- `ready`
- `in-progress`
- `blocked`
- `done`
- `deferred`

## `docs/decisions/ADR-XXXX-title.md`

Purpose: explain a load-bearing decision.

Required fields:

- status,
- date,
- context,
- decision,
- alternatives considered,
- consequences,
- follow-up work.

Recommended statuses:

- `proposed`
- `accepted`
- `superseded`
- `deprecated`

## `docs/specs/<change>.md`

Purpose: implementation contract.

Required sections:

- status,
- problem,
- outcome,
- non-goals,
- dependencies / ADRs,
- design,
- failure behavior,
- acceptance criteria,
- verification plan,
- test plan,
- open questions.

Recommended statuses:

- `draft`
- `ready`
- `in-progress`
- `implemented`
- `verified`
- `done`

## `docs/evidence/<change>.md`

Purpose: proof that the changed system was exercised.

Required sections:

- date,
- environment,
- revision or branch when known,
- commands run,
- acceptance-criteria results,
- manual checks,
- automated checks,
- failures / limitations,
- final verification status.

## `docs/reviews/<change>.md`

Purpose: independent review findings.

Each finding should contain:

- severity,
- affected file or surface,
- finding,
- impact,
- recommended action,
- status.
