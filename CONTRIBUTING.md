# Contributing

Thanks for helping improve ContextForge Skills.

## Contribution rules

1. Keep each skill focused on one primary job.
2. Do not add instructions that contradict another skill's ownership boundaries.
3. Prefer repository artifacts over hidden conversational state.
4. New workflow rules must define:
   - trigger,
   - inputs,
   - outputs,
   - stop conditions,
   - handoff.
5. Avoid product-specific assumptions unless they are examples.
6. Keep skill descriptions concise because agents use them for discovery.
7. Test new or changed skills with at least three prompts:
   - one that should trigger the skill,
   - one borderline prompt,
   - one that should not trigger the skill.

## Pull request checklist

- [ ] The skill has a valid `SKILL.md`.
- [ ] YAML front matter contains `name` and `description`.
- [ ] The skill defines what it owns and what it must not own.
- [ ] Durable outputs have explicit paths.
- [ ] Handoffs to other skills are explicit.
- [ ] No copied proprietary content was added.
- [ ] README or workflow documentation was updated when behavior changed.
