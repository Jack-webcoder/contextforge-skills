---
name: decide
description: Resolve a load-bearing architecture, product, provider, data, security, or platform choice and record it as an ADR in docs/decisions. Use when implementation would otherwise require inventing a consequential decision.
---

# Decide a Load-Bearing Choice

## Purpose

Resolve one important technical or product decision and record the reasoning as an Architecture Decision Record (ADR).

## Use when

Implementation depends on a choice that future code or product behavior will rely on, including:

- framework or runtime,
- database or persistence strategy,
- authentication or authorization,
- third-party provider,
- public API contract,
- global state ownership,
- data model,
- security boundary,
- cross-cutting UX behavior,
- deployment architecture,
- migration strategy.

## Do not use when

The choice is a small, local implementation detail that follows existing conventions.

## Inputs

Read:

- `AGENTS.md`,
- `PROJECT_CONTEXT.md`,
- `docs/scope/ROADMAP.md`,
- related ADRs,
- related specs,
- relevant source code when the project already exists.

## Procedure

1. State the decision question in one sentence.
2. Explain why the decision is needed now.
3. Identify project constraints that materially affect the answer.
4. Present realistic alternatives, including keeping the current approach when applicable.
5. Compare alternatives on criteria relevant to this project.
6. Make a recommendation.
7. When user input is required, ask for the decision rather than silently choosing.
8. Write the accepted outcome to the next numbered file under `docs/decisions/` using `ADR-XXXX-title.md`.
9. Set status to `proposed` until the choice is actually accepted; use `accepted` only after approval is clear.
10. Record consequences and follow-up work.

## Rules

- Do not hide trade-offs.
- Do not select technology because it is merely popular.
- Do not invent constraints.
- Do not rewrite an accepted ADR in place to reverse history. Create a superseding ADR and update status links.
- A decision may be proposed by the agent but must be explicit and durable before dependent implementation begins.

## Completion criteria

The ADR makes it possible for a future agent to answer:

- What was decided?
- Why?
- What alternatives were rejected?
- What trade-offs were accepted?
- What future work depends on this choice?

## Handoff

After an accepted decision, run `spec` for the feature or change that depends on it.
