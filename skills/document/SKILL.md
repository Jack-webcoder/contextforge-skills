---
name: document
description: Write accurate PR text, changelog entries, release notes, or postmortems from the actual diff, decisions, tests, verification evidence, and review. Use after implementation; do not describe planned or unverified work as shipped.
---

# Document the Actual Change

## Purpose

Write human-facing change documentation from the real implementation, evidence, and review rather than from an early plan.

## Use when

- preparing a pull request,
- updating a changelog,
- writing release notes,
- writing a postmortem after an incident.

## Inputs

Read:

- actual diff or changed files,
- relevant spec,
- ADRs,
- evidence,
- review findings,
- test results.

## Procedure

1. Determine the requested document type.
2. Base claims on the actual diff and recorded evidence.
3. Explain user-visible and engineering impact.
4. Mention migrations, configuration changes, or compatibility concerns.
5. Mention known limitations honestly.
6. Include verification and test summary where useful.
7. Write to the repository's existing convention when one exists.

## Suggested outputs

- PR body: return ready-to-paste Markdown or write to an explicitly requested file.
- Changelog: update `CHANGELOG.md` when the project uses one.
- Release note: `docs/releases/<version-or-date>.md`.
- Postmortem: `docs/postmortems/<incident>.md`.

## Rules

- Do not claim a feature is verified when evidence says partial or failed.
- Do not describe planned work as shipped work.
- Prefer concrete behavior over marketing language unless marketing copy is explicitly requested.

## Handoff

Run `sync` after documentation is complete.
