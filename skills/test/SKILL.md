---
name: test
description: Add automated regression coverage for implemented or fixed behavior, prioritizing acceptance criteria and bug regressions, then run the relevant test suite and update verification evidence. Use after verify or debug.
---

# Add Regression Protection

## Purpose

Create or improve automated tests that protect the behavior introduced or fixed by the current change.

## Use when

- a feature has been implemented,
- a bug has been fixed,
- verified behavior needs durable regression coverage.

## Inputs

Read:

- relevant spec,
- verification evidence,
- changed implementation,
- existing test framework and test conventions,
- `AGENTS.md`.

## Procedure

1. Identify the highest-value behaviors to protect.
2. Prefer tests that map directly to acceptance criteria or the reproduced bug.
3. Reuse the project's existing test framework.
4. Follow existing test placement and naming conventions.
5. Cover failure paths and boundaries when risk justifies them.
6. Avoid testing private implementation details when observable behavior is available.
7. Run the relevant tests.
8. Record the command and result in the existing evidence artifact when one exists.
9. If a test exposes a real defect, do not weaken the test to make it pass; hand the defect to `debug` or `build`.

## Priority order

1. Regression case for a fixed bug.
2. Acceptance criteria.
3. High-risk branches.
4. Failure behavior.
5. Cross-module boundaries.

## Completion criteria

- Meaningful regression coverage exists.
- Relevant tests have been run when the environment permits.
- Results are reflected in evidence.

## Handoff

- Test failure caused by product defect → `debug`.
- Standard workflow → `sync`.
- Strict workflow → `review`.
