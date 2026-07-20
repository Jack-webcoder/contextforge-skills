---
name: debug
description: Reproduce a bug, isolate and prove the root cause, apply the smallest safe fix, verify the original failure is resolved, and hand a regression case to test. Use for broken or incorrect behavior; route undefined behavior to spec and new architecture choices to decide.
---

# Debug by Root Cause

## Purpose

Reproduce a failure, identify its root cause, apply the smallest safe root-cause fix, and preserve regression evidence.

## Use when

Something is failing, crashing, producing incorrect behavior, or violating a previously working contract.

## Inputs

Read:

- bug report or observed symptom,
- `AGENTS.md`,
- `PROJECT_CONTEXT.md`,
- relevant specs and ADRs,
- recent evidence and reviews,
- relevant source and tests.

## Root-cause loop

1. **Reproduce** — establish a reliable failing case.
2. **Narrow** — reduce the failing surface.
3. **Hypothesize** — state a falsifiable explanation.
4. **Test the hypothesis** — gather evidence.
5. **Fix the root cause** — prefer the smallest safe change.
6. **Verify** — rerun the reproduction and affected behavior.
7. **Protect** — hand the regression case to `test`.

## Rules

- Do not begin with random edits.
- Preserve useful failing logs and observations.
- Separate correlation from root cause.
- Do not broaden the fix into unrelated refactoring unless necessary for correctness.
- If the correct fix requires a new load-bearing decision, stop and run `decide`.
- If expected behavior is undefined, stop and run `spec`.

## Evidence

Create or update `docs/evidence/<bug-or-change-name>.md` with:

- reproduction steps,
- observed failure,
- root cause,
- fix summary,
- post-fix verification.

## Completion criteria

- The original failure is reproducible before the fix when practical.
- Root cause is explained.
- The fix addresses the cause, not only the symptom.
- The failing case passes after the fix.

## Handoff

Run `test` to add a regression test, then `sync`.
