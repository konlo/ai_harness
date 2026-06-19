# JUDGE Template

JUDGE is an independent RTM-only decision. It reads only `docs/rtm.md`.

If evidence, review, or loopback details are needed for judgment, they must be
summarized in the RTM before JUDGE starts. JUDGE must not inspect linked reports,
the codebase, or chat history directly.

## Header

- **Req ID**:
- **Date**:
- **Judge**:
- **RTM Row**:

## Inputs Read

- `docs/rtm.md`:

## Checks

| Check | PASS / FAIL | Evidence |
| --- | --- | --- |
| Success criteria satisfied |  |  |
| Constraints verified or waived |  |  |
| Real E2E artifact present or waiver approved |  |  |
| Mocked E2E not used as real PASS |  |  |
| No unresolved CRITICAL / BLOCKER review issue |  |  |
| Loopback limits not exceeded |  |  |
| RTM has design, test, implementation, evidence links |  |  |

## Decision

- **Decision**: PASS / LOOPBACK / PARTIAL
- **Loopback Target**: P3 / P4 / P5 / P6 / None
- **Classification**:
- **Reason**:
- **Required RTM Update**:

## Rules

- Missing required evidence cannot PASS.
- FAIL evidence cannot PASS.
- Mocked E2E cannot PASS real boundary behavior without waiver.
- Evidence and review details not summarized in RTM are treated as missing.
- Requirement changes start a new cycle.
- Loopback limits exceeded means PARTIAL report.
