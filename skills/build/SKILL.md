---
name: build
description: Implement an approved spec or low-risk Quick change while enforcing decision and specification gates. Use for production code changes; stop and route to decide or spec when consequential choices or requirements are missing.
---

# Build from the Contract

## Purpose

Implement an approved change while respecting repository context, accepted decisions, and the feature specification.

## Use when

A spec is ready or the requested change is genuinely small enough for the project's `Quick` workflow.

## Inputs

Read before editing:

- `AGENTS.md`,
- `PROJECT_CONTEXT.md`,
- the relevant spec when one exists,
- linked ADRs,
- relevant existing code and tests.

## Pre-build gate

Before coding, ask:

1. Is the intended behavior clear?
2. Is every load-bearing decision already recorded?
3. Does implementation follow existing project boundaries?
4. Are acceptance criteria available for a meaningful feature?

If a consequential decision is missing, stop and hand off to `decide`.

If a meaningful feature lacks a usable spec, stop and hand off to `spec`.

## Procedure

1. Mark the relevant spec `in-progress` when appropriate.
2. Inspect the smallest relevant code surface first.
3. Implement the smallest coherent change that satisfies the contract.
4. Follow existing patterns unless an accepted ADR explicitly changes them.
5. Add migrations or generated artifacts only when required by the spec.
6. Run the repository's configured static checks that are practical in the environment.
7. Fix issues introduced by the change.
8. Summarize changed files and any explicit low-risk assumptions.

## Allowed implementation judgment

You may choose ordinary local details such as:

- names,
- helper extraction,
- control-flow structure,
- small component decomposition,
- private function signatures.

You may not silently choose:

- a new provider,
- a new database strategy,
- a new auth model,
- a new public API,
- a new global state architecture,
- an irreversible migration strategy.

## Completion criteria

- The code is implemented.
- Configured static checks pass, or failures are documented.
- No acceptance criterion is knowingly ignored.
- No hidden load-bearing decision was invented.

## Handoff

Run `verify` next.
