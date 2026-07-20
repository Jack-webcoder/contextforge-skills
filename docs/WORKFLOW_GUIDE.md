# Workflow Guide

## 1. Start with the repository, not the chat

Before doing meaningful work, the active skill should inspect the durable project artifacts that are relevant to its phase.

At minimum, most implementation-related skills should look for:

- `AGENTS.md`
- `PROJECT_CONTEXT.md`
- `docs/scope/ROADMAP.md`
- relevant `docs/decisions/*.md`
- relevant `docs/specs/*.md`

The repository is the source of truth. Chat context is helpful but not authoritative when it conflicts with committed project artifacts.

## 2. Greenfield workflow

### Phase A — Scope

Run `$scope` with the product idea.

Output:

- product goal,
- target users,
- in-scope / out-of-scope boundaries,
- milestones,
- next slice,
- default workflow depth.

### Phase B — Decide the foundation

Run `$decide` for load-bearing choices such as stack, persistence, auth, deployment, or provider strategy.

Each important decision becomes an ADR in `docs/decisions/`.

### Phase C — Scaffold

Create the real project using the selected architecture.

### Phase D — Bootstrap context

Run `$bootstrap` so the workflow reads the actual repository instead of an imagined structure.

### Phase E — Feature loop

For each meaningful feature:

```text
$spec → $build → $verify → $test → $sync
```

Add `$review` and `$document` for strict or release-critical work.

## 3. Existing project workflow

Start with `$bootstrap`.

It should discover the actual:

- stack,
- package manager,
- commands,
- source layout,
- test framework,
- style conventions,
- architectural patterns,
- important constraints.

Then run `$scope` to define the next slice of work.

## 4. Decision gate

Before coding, ask:

> Would implementing this require choosing something that future code will depend on?

If yes, check whether the decision already exists in:

- `AGENTS.md`,
- `PROJECT_CONTEXT.md`,
- an ADR,
- an approved spec.

If not, stop and run `$decide`.

## 5. Specification contract

A spec is implementation-ready only when it includes:

- problem statement,
- desired behavior,
- non-goals,
- dependencies on existing ADRs,
- affected surfaces,
- data flow,
- failure behavior,
- acceptance criteria,
- test notes,
- unresolved questions.

Unresolved questions that affect implementation must be resolved before `$build`.

## 6. Build phase

`$build` is allowed to make ordinary implementation choices that do not alter project architecture.

Examples:

- local variable names,
- small helper extraction,
- internal control flow,
- obvious component decomposition that follows existing conventions.

`$build` is not allowed to silently choose:

- a new database,
- a new auth system,
- a new external provider,
- a new global state architecture,
- an irreversible migration design,
- a new public API contract not covered by the spec.

## 7. Verify phase

`$verify` runs the changed system against the acceptance criteria.

It writes an evidence record containing:

- change identifier,
- environment,
- commands,
- manual flows,
- results for each criterion,
- screenshots or logs when available,
- known limitations.

A failed criterion returns the work to `$build` or `$debug`.

## 8. Test phase

`$test` turns the verified behavior into automated protection where appropriate.

Tests should prioritize:

1. acceptance criteria,
2. bug regressions,
3. high-risk branches,
4. failure paths,
5. boundaries between components or services.

## 9. Review phase

`$review` should be independent in mindset. It is not a continuation of implementation.

It asks:

- Is the spec actually satisfied?
- Did implementation violate an ADR?
- Is there hidden complexity or risk?
- Are errors handled correctly?
- Are tests meaningful?
- Is there security, privacy, performance, accessibility, or maintainability risk?

## 10. Debug phase

`$debug` follows a root-cause loop:

```text
reproduce → narrow → hypothesize → test hypothesis → fix root cause → verify → hand regression case to $test
```

Do not patch symptoms when the root cause is known and safely fixable.

## 11. Sync phase

`$sync` reconciles durable project truth with reality.

It may update:

- `PROJECT_CONTEXT.md`,
- `AGENTS.md`,
- roadmap statuses,
- spec statuses,
- ADR status references,
- evidence links.

It must not rewrite history to make an incomplete feature look complete.
