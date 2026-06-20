# Repository Agent Instructions

`CLAUDE.md` is the primary local behavior guide for this repository.

Before making changes, agents must:

1. Read `CLAUDE.md`.
2. Apply its four principles first for repository-local behavior:
   - Think Before Coding
   - Simplicity First
   - Surgical Changes
   - Goal-Driven Execution
3. Then read task-specific project files such as `README.md`,
   `generic_harness/README.md`, and relevant runbooks.

If repository documents appear to conflict:

- Higher-priority platform, system, or developer instructions still take
  precedence.
- For local project behavior, prefer `CLAUDE.md` unless a more specific file
  explicitly narrows the task scope.
- Do not use harness process documents as permission to over-engineer a simple
  change; follow `CLAUDE.md`'s simplicity and surgical-change rules.

For HALO harness work, combine `CLAUDE.md` with:

- `generic_harness/docs/runbooks/halo_operating_flow.md`
- `generic_harness/docs/runbooks/orchestrator_agent_flow.md`
- `generic_harness/docs/rtm.md`
