---
name: scope
description: Define or update product scope, milestones, boundaries, and the next shippable slice in docs/scope/ROADMAP.md. Use for new products or planning work; do not use for detailed technical design or coding.
---

# Scope Product Work

## Purpose

Turn a product idea or a new slice of work into a living roadmap with explicit boundaries and priorities.

## Use when

- starting a new product,
- planning the next milestone,
- reducing an oversized idea into a shippable slice,
- checking what is planned, in progress, blocked, or done.

## Inputs

Read when present:

- `PROJECT_CONTEXT.md`,
- `AGENTS.md`,
- `docs/scope/ROADMAP.md`,
- relevant completed specs,
- relevant accepted ADRs.

## Procedure

1. Restate the desired product outcome in observable terms.
2. Identify target users or actors.
3. Separate in-scope work from non-goals.
4. Break work into milestones based on dependency order, not excitement order.
5. Define the smallest meaningful next slice.
6. Assign a workflow depth: `Quick`, `Standard`, or `Strict`.
7. Mark dependencies and blockers.
8. Write or update `docs/scope/ROADMAP.md`.
9. Do not turn the roadmap into a detailed implementation spec.

## Roadmap rules

Use statuses:

- `planned`
- `ready`
- `in-progress`
- `blocked`
- `done`
- `deferred`

Only mark work `done` when repository evidence supports completion.

## Decision boundary

If the next slice depends on an unresolved load-bearing decision, record the dependency and hand off to `decide`.

Examples:

- choose local storage versus server database,
- choose auth strategy,
- define public API ownership,
- choose AI provider abstraction,
- choose migration strategy.

## Completion criteria

The roadmap clearly answers:

- What are we building?
- What are we not building now?
- What comes next?
- Why is that the next slice?
- What blocks it?
- How rigorous should the workflow be?

## Handoff

- Missing decision → `decide`.
- Decisions already exist and next change needs an implementation contract → `spec`.
