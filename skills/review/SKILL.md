---
name: review
description: Perform an independent senior review of a completed change against its spec, ADRs, tests, evidence, security, correctness, and maintainability, then write findings to docs/reviews. Use for Strict or high-risk work.
---

# Review Independently

## Purpose

Perform a senior, independent review of the change against the specification, decisions, evidence, and project constraints.

## Use when

- the workflow depth is `Strict`,
- the change is risky or cross-cutting,
- a release or pull request needs a formal review artifact.

## Inputs

Read:

- `AGENTS.md`,
- `PROJECT_CONTEXT.md`,
- relevant spec,
- linked ADRs,
- verification evidence,
- tests,
- the actual diff or changed files.

## Review dimensions

Check:

1. Contract correctness — does the change satisfy the spec?
2. Decision compliance — does it follow accepted ADRs?
3. Hidden decisions — did implementation quietly introduce a new architecture choice?
4. Failure handling — are errors and edge cases handled?
5. Data integrity — can state become inconsistent?
6. Security and privacy — are boundaries and sensitive data handled correctly?
7. Performance — are there obvious high-impact regressions?
8. Accessibility and UX — where relevant.
9. Maintainability — is complexity justified?
10. Tests — do they protect behavior rather than merely mirror implementation?
11. Evidence — was the important behavior actually exercised?

## Procedure

1. Review the diff with a skeptical mindset.
2. Trace each acceptance criterion to implementation and evidence.
3. Record findings by severity.
4. Distinguish blockers from optional improvements.
5. Write `docs/reviews/<change-name>.md`.
6. Set overall status to `pass`, `changes-requested`, or `blocked`.

## Rules

- Do not rewrite implementation while reviewing unless the user explicitly asks for review-and-fix.
- Do not invent findings to appear thorough.
- Cite exact files, lines, or behaviors where possible.
- A missing proof of correctness is a review concern when the behavior is important.

## Handoff

- Blocking finding → `build` or `debug`.
- Passing strict review → `document`, then `sync`.
