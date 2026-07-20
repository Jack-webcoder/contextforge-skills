# Example: applying ContextForge to a project

This directory shows only the durable artifact layout. It is not an application.

```text
AGENTS.md
PROJECT_CONTEXT.md
docs/
├── scope/ROADMAP.md
├── decisions/ADR-0001-storage.md
├── specs/offline-notes.md
├── evidence/offline-notes.md
└── reviews/offline-notes.md
```

A typical sequence:

1. `$bootstrap` creates project context.
2. `$scope` identifies "offline notes" as the next slice.
3. `$decide` records the storage choice.
4. `$spec` defines observable behavior.
5. `$build` implements it.
6. `$verify` records runtime evidence.
7. `$test` adds regression coverage.
8. `$review` checks high-risk concerns.
9. `$sync` reconciles status.
