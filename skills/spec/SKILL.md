---
name: spec
description: Create an implementation-ready feature or change specification in docs/specs with explicit acceptance criteria, failure behavior, verification, and test plans. Use after scope and decisions are settled; route unresolved load-bearing choices to decide.
---

# Specify a Change

## Purpose

Turn an approved product slice into an implementation-ready contract that later skills can execute and verify.

## Use when

- a feature or meaningful change is ready to design,
- implementation spans multiple files or behaviors,
- acceptance criteria need to be explicit,
- a previous vague request must become buildable.

## Inputs

Read:

- `AGENTS.md`,
- `PROJECT_CONTEXT.md`,
- `docs/scope/ROADMAP.md`,
- all ADRs relevant to the change,
- related existing specs,
- relevant source code for brownfield work.

## Procedure

1. Define the current problem.
2. Define the observable desired outcome.
3. State explicit non-goals.
4. Link every relevant accepted ADR.
5. Identify affected surfaces.
6. Describe the design at enough detail for implementation without re-deciding architecture.
7. Trace important data from source to destination.
8. Define failure and edge-case behavior.
9. Write testable acceptance criteria.
10. Define how each criterion can be verified in the real system.
11. Define the automated test plan.
12. List open questions.
13. If any open question changes architecture, provider choice, persistence, security, or public contract, stop and hand off to `decide`.
14. Write the spec to `docs/specs/<change-name>.md` and set status to `ready` only when no implementation-blocking question remains.

## Acceptance criteria rules

Good criteria are observable.

Weak:

- "The page works well."

Strong:

- "When a signed-out user opens `/settings`, the app redirects to `/login` without rendering protected account data."

## Completion criteria

A developer or coding agent can implement the change without inventing a load-bearing decision.

## Handoff

- Missing decision → `decide`.
- Ready spec → `build`.
