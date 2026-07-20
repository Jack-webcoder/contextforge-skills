---
name: bootstrap
description: Inspect an existing or scaffolded repository and create durable project context in AGENTS.md and PROJECT_CONTEXT.md. Use before other workflow skills when project context is missing or stale; do not use to design or implement features.
---

# Bootstrap Project Context

## Purpose

Inspect the actual repository and establish durable context for all later skills.

## Use when

- ContextForge is being adopted in an existing codebase.
- A greenfield project has been scaffolded and now has real files to inspect.
- `AGENTS.md` or `PROJECT_CONTEXT.md` is missing or materially stale.

## Do not use when

- The task is to design a new feature. Use `spec` or `decide`.
- The task is to implement code. Use `build`.

## Inputs

Inspect the repository before writing anything. Look for:

- package manifests and lockfiles,
- framework and runtime configuration,
- source directories,
- build, lint, type-check, and test commands,
- CI configuration,
- existing documentation,
- existing `AGENTS.md`,
- persistence and migrations,
- environment-variable examples,
- external integrations,
- testing patterns,
- coding conventions visible in representative files.

## Procedure

1. Determine the repository root and target workspace.
2. Read existing durable instructions before proposing replacements.
3. Identify the actual stack from files, not assumptions.
4. Identify commands that are demonstrably configured.
5. Map the important directories and architectural boundaries.
6. Identify external systems and persistence.
7. Identify conventions that are repeated enough to be real conventions.
8. Create or update `PROJECT_CONTEXT.md` using `templates/PROJECT_CONTEXT.md` as a structural reference when available.
9. Create or update a concise `AGENTS.md` containing only durable instructions that agents should read before work.
10. Preserve existing human-authored rules unless they are clearly obsolete. When uncertain, flag the conflict instead of deleting the rule.

## Rules

- Never invent a command because it is common for the framework.
- Never claim a service exists unless repository evidence supports it.
- Prefer exact file paths and exact command names.
- Keep `AGENTS.md` concise; put descriptive context in `PROJECT_CONTEXT.md`.
- Do not make architectural decisions. Record unresolved architecture as an open item and hand it to `decide`.

## Completion criteria

The skill is complete when a fresh agent session can determine:

- what the project is,
- how to install and run it,
- how to validate changes,
- where important code lives,
- what boundaries must not be violated,
- where decisions, specs, and evidence are stored.

## Handoff

- New product with no roadmap → `scope`.
- Missing load-bearing architecture → `decide`.
- Ready feature request → `spec`.
