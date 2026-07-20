---
name: sync
description: Reconcile AGENTS.md, PROJECT_CONTEXT.md, roadmap, spec statuses, ADR references, reviews, and verification evidence with the repository's actual state. Use as the final workflow step; never mark work done without supporting evidence.
---

# Sync Repository Truth

## Purpose

Reconcile durable project knowledge with the repository's actual current state after a change.

## Use when

- finishing a feature,
- finishing a bug fix,
- preparing to merge,
- project context or roadmap status has drifted.

## Inputs

Read:

- `AGENTS.md`,
- `PROJECT_CONTEXT.md`,
- roadmap,
- relevant ADRs,
- relevant specs,
- evidence,
- reviews,
- actual changed code and tests.

## Procedure

1. Compare the implementation with the relevant spec.
2. Compare verification status with acceptance criteria.
3. Compare tests with the promised test plan.
4. Update spec status truthfully:
   - `implemented` when code exists,
   - `verified` when required behavior is verified,
   - `done` only when the project's selected workflow depth is satisfied.
5. Update roadmap item status based on actual completion.
6. Update `PROJECT_CONTEXT.md` when architecture, integrations, commands, or repository layout materially changed.
7. Update `AGENTS.md` only for durable instructions that future agents must always know.
8. Add links between specs, decisions, evidence, and reviews when useful.
9. Do not erase unresolved limitations or failed evidence.

## Rules

- Sync is reconciliation, not a summary-writing exercise.
- The implementation is authoritative about what exists.
- Accepted ADRs are authoritative about why load-bearing choices exist until superseded.
- Evidence is authoritative about what has actually been verified.
- Never mark `done` merely because code was written.

## Completion criteria

A fresh agent session can inspect the repository and accurately understand:

- current architecture,
- current roadmap status,
- decision history,
- feature status,
- verification state,
- remaining limitations.
