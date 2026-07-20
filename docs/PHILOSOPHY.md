# Philosophy

## The problem

AI agents often fail in project-specific ways even when their code is technically reasonable. Common causes include:

- a decision existed only in an old chat,
- a new session did not know an architectural constraint,
- an agent selected a generic provider, library, or data model,
- a feature was declared complete without running the real workflow,
- documentation drifted away from the implementation.

## The ContextForge answer

ContextForge treats a software repository as a shared memory system.

There are four kinds of durable truth:

1. **Context** — what this project is and how it is built.
2. **Decisions** — why important choices were made.
3. **Contracts** — what a specific change must accomplish.
4. **Evidence** — what was actually run and observed.

A coding agent should not need a perfect conversation history if these four forms of truth are maintained.

## Ownership model

Each artifact has a primary owner:

- `AGENTS.md` and `PROJECT_CONTEXT.md` → `bootstrap`, maintained by `sync`
- `docs/scope/` → `scope`, status reconciled by `sync`
- `docs/decisions/` → `decide`
- `docs/specs/` → `spec`, status reconciled by `sync`
- application code → `build` / `debug`
- `docs/evidence/` → `verify`, extended by `test`
- tests → `test`
- `docs/reviews/` → `review`
- release notes / changelog / PR text → `document`

Skills may read artifacts owned by other skills. They should not casually rewrite another skill's core artifact.

## The decision gate

A load-bearing decision includes choices such as:

- framework or runtime,
- database or schema strategy,
- authentication provider,
- external service provider,
- API boundary,
- state ownership,
- security model,
- persistence model,
- cross-cutting UX pattern,
- irreversible migration strategy.

When implementation requires one of these choices and the choice is not already recorded, `build` must stop and route to `decide`.

## The evidence gate

A feature is not verified merely because:

- the code compiles,
- a diff looks correct,
- an agent says it should work.

Verification should record concrete evidence such as:

- command executed,
- environment used,
- user flow exercised,
- expected result,
- actual result,
- remaining gaps.

## Assumptions

Small local assumptions are sometimes necessary. They must be:

- explicit,
- reversible,
- low risk,
- recorded in the relevant spec or evidence artifact.

An assumption that changes architecture, product behavior, security, persistence, or external-provider choice is not a small assumption. It requires `decide`.
