# Project Agent Guidelines

Replace bracketed placeholders before use.

## Project Context

- **Product / System**: `[describe what is being built]`
- **Core Goal**: `[primary outcome]`
- **Validation Goal**: `[how correctness is proven]`
- **Primary Tech Stack**: `[languages, frameworks, tools]`

## Responsibility Boundaries

- **Domain / Core**: business rules, state transitions, deterministic behavior.
- **Interface / UI / API**: rendering, inputs, adapters, request/response mapping.
- **Validation**: scenarios, runners, fixtures, artifacts, regression checks.
- **Orchestrator**: RTM, gates, phase outputs, delegation, evidence review, loopback decisions.
- **JUDGE**: RTM-only PASS / LOOPBACK / PARTIAL decision.

Do not move rules into UI/API layers. Do not patch tests to hide product
defects. Do not call mocked E2E a PASS when real E2E is required.

## Required Workflow

For medium/high-risk changes:

```text
P1 -> P2 -> P3 -> P4 -> P5 -> P6 -> P7 -> P8 -> JUDGE -> Final Approval Gate -> P9
```

1. Define the requirement in `docs/rtm.md`.
2. Run P1 constraint verification for external assumptions.
3. Write phase outputs using `docs/phase_templates/`.
4. Record required approvals or waivers in `docs/gate_checklist.md`.
5. Implement only inside the scope approved by the phase output and contract.
6. Record real validation artifacts in `docs/e2e_evidence_log.md`.
7. Run P8 Quality, Bug, and Security/Contract review.
8. Run JUDGE from `docs/rtm.md` only.
9. If JUDGE returns LOOPBACK, update `docs/loopback_log.md` before more edits.
10. If JUDGE returns PASS or PARTIAL, record Final Approval Gate.
11. Record final or partial outcome in `docs/reports/` and `project_progress.md`.

## File = Interface

Phase handoff happens through files, not chat history.

- Each phase must name its input files and output file.
- Each phase must update the RTM fields it owns.
- A restarted session must be able to continue from RTM plus linked files.
- Requirement changes start a new cycle; they are not loopbacks.

## Logging Rule

Append one entry per user request to `project_progress.md`:

```md
### [YYYY-MM-DD HH:MM:SS TZ] User Request: <summary>
- **Skills Planned**: []
- **Skills Used**: []
- **Trigger Reason**: "<why this workflow was used>"
- **Req ID**: ""
- **Phase Range**: ""
- **Files Touched**: []
- **Validation**: "<what was checked>"
- **Judge Decision**: "PASS / LOOPBACK / PARTIAL / Not run"
- **Outcome**: "<result and residual risk>"
```
