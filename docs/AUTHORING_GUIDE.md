# Skill Authoring Guide

## Skill shape

Each skill lives in its own directory and must contain `SKILL.md`.

```text
skills/
└── example/
    ├── SKILL.md
    └── agents/
        └── openai.yaml
```

Optional directories such as `scripts/`, `references/`, and `assets/` can be added when needed.

## Front matter

Use a stable lowercase hyphenated name and a concise trigger-oriented description.

```yaml
---
name: example-skill
description: Do X when Y. Do not use for Z.
---
```

## Instruction design

A strong skill should explicitly define:

1. **Purpose** — one primary job.
2. **Trigger** — when to use it.
3. **Do not use** — boundaries.
4. **Inputs** — files and user intent to inspect.
5. **Procedure** — imperative steps.
6. **Decision rules** — stop / continue criteria.
7. **Outputs** — exact durable artifacts.
8. **Completion criteria** — when the skill is done.
9. **Handoff** — which skill should run next.

## Progressive disclosure

Keep the `description` short enough for skill discovery. Put detailed workflow instructions in `SKILL.md`. Put long reference material in `references/` when the skill becomes too large.

## Avoid hidden state

Never require future skills to remember a decision that exists only in the active conversation.

## Scripts

Use scripts only when deterministic automation is better than natural-language instructions. Examples:

- validating required artifact sections,
- generating the next ADR number,
- checking broken internal links.

Do not add scripts merely to make the repository look sophisticated.
