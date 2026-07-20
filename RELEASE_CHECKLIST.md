# Release Checklist

Before publishing the repository:

- [ ] Replace `YOUR_GITHUB_USERNAME` in README examples if desired.
- [ ] Confirm repository name.
- [ ] Review the MIT copyright holder.
- [ ] Run `npx skills@latest add ./contextforge-skills --list` from the parent directory.
- [ ] Install locally and confirm all skills appear.
- [ ] Trigger each skill explicitly once.
- [ ] Test at least one implicit-trigger prompt per skill.
- [ ] Verify `AGENTS.md` and `PROJECT_CONTEXT.md` are not overwritten destructively in a sample project.
- [ ] Create the GitHub repository.
- [ ] Push `main`.
- [ ] Test public install with `npx skills@latest add <owner>/contextforge-skills --list`.
- [ ] Create `v0.1.0` release after the public install works.
