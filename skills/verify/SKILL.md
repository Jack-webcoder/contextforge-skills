---
name: verify
description: Run the real changed system against acceptance criteria and record commands, observations, and pass/fail evidence in docs/evidence. Use after build or debug; do not treat code inspection alone as runtime verification.
---

# Verify Real Behavior

## Purpose

Exercise the changed system against its acceptance criteria and record concrete evidence.

## Use when

- implementation is complete enough to run,
- a bug fix needs proof,
- behavior must be checked before tests or review,
- a change is being considered complete.

## Inputs

Read:

- relevant spec,
- acceptance criteria,
- `AGENTS.md`,
- relevant ADRs,
- changed files,
- existing evidence if verification is being repeated.

## Procedure

1. Identify every acceptance criterion.
2. Determine the real command or user flow that can exercise each criterion.
3. Run the configured application, service, CLI, or workflow when the environment permits.
4. Record exact commands executed.
5. Record the environment and revision when known.
6. For each criterion, record `pass`, `fail`, or `blocked` with observed evidence.
7. Run relevant existing automated checks when they are part of realistic verification.
8. Write or update `docs/evidence/<change-name>.md`.
9. Set final verification status to:
   - `verified` only when required criteria pass,
   - `failed` when behavior is wrong,
   - `partial` when meaningful checks are blocked.

## Rules

- Do not replace runtime verification with code inspection when the system can reasonably be run.
- Do not claim a command passed unless it was actually executed in the current environment or evidence is explicitly imported from a trusted external run.
- Separate "not tested" from "passed."
- Preserve failure evidence; it is useful for debugging.

## Completion criteria

The evidence record lets another person understand what was run and why the verification status is justified.

## Handoff

- Functional failure → `debug` or `build`.
- Verified behavior needing regression protection → `test`.
- Quick low-risk change with sufficient verification → `sync`.
