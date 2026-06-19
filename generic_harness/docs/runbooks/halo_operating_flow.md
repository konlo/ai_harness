# HALO Operating Flow

This runbook makes AI-assisted work follow a controlled engineering loop:

```text
P1 -> P2 -> P3 -> P4 -> P5 -> P6 -> P7 -> P8 -> JUDGE -> Final Approval Gate -> P9
```

The RTM is the single source of truth. Files are the interface between phases.

## Phase Contract

Each phase must define:

- input files it is allowed to read
- output file it will create or update
- RTM fields it must update
- gate or stop condition, if any
- evidence required before the next phase

Use `docs/phase_templates/` for phase checklists.

## 9 Phases

| Phase | Name | Required Output | RTM Responsibility |
| --- | --- | --- | --- |
| P1 | Requirements + Constraint Verification | requirement brief and constraint verification | create Req ID, success criteria, external assumptions |
| P2 | Exploration | exploration notes | map relevant files, systems, constraints |
| P3 | Architecture | architecture decision | link design and affected contracts |
| P4 | Unit Test Design | unit test plan or test changes | map unit tests to Req ID |
| P5 | Implementation | code changes | record implementation locations |
| P6 | Integration / E2E Test Design | integration or E2E plan | map real validation scenario |
| P7 | Test Execution + Evidence | test artifacts | record PASS/FAIL and evidence path |
| P8 | Code Review x3 | review reports | record Quality, Bug, Security/Contract issues |
| P9 | Final / Partial Report | final report | close RTM status |

JUDGE is not a phase. It is an independent RTM-only subagent that runs after P8
and before the Final Approval Gate.

## Required Gates

Gate is for human direction, not just mechanical validation.

- Requirement Gate: after P1 when scope or intent can be wrong.
- Architecture Gate: after P3 when design direction is expensive to reverse.
- Real E2E Waiver Gate: before skipping required real validation.
- Final Approval Gate: after JUDGE returns PASS or PARTIAL and before P9.

Record every gate in `docs/gate_checklist.md`.

## Constraint Verification

P1 must verify external assumptions before design starts:

- API endpoints exist and can be called.
- Database, service, or device access is available.
- Required library/tool versions are installed or installable.
- Permissions, credentials, network, simulator, or environment assumptions hold.

Unverified assumptions stay as assumptions. They cannot become PASS evidence.

## Real E2E Policy

Mocked E2E is not PASS when the requirement crosses UI, API, network, device,
model, service, or process boundaries.

- Real E2E must produce artifact paths under `test_artifacts/` or an equivalent
  project artifact directory.
- If real E2E cannot run, create a Real E2E Waiver Gate with residual risk.
- Missing artifacts are inconclusive, not PASS.

## File = Interface

Do not rely on long chat history as the phase handoff.

- Write phase outputs under `docs/agent_tasks/active/` or a project-specific
  durable docs directory.
- Link outputs from the RTM.
- A restarted agent should read the RTM, the current phase output, and this
  runbook before continuing.
- `.workflow/` may hold temporary checkpoints but must not be the only copy of
  a required decision.

## P8 Review

P8 uses three independent review perspectives:

- Quality: maintainability, duplication, readability, local conventions.
- Bugs: logic errors, edge cases, state transitions, regressions.
- Security/Contract: security, public contracts, external dependencies,
  privacy, mock-only success.

Record MAJOR/CRITICAL review findings in the RTM before JUDGE.

## JUDGE

JUDGE reads only `docs/rtm.md`. It does not read the full codebase, chat history,
or linked reports directly. Evidence, review, and loopback details needed for
judgment must be summarized in RTM fields before JUDGE runs.

JUDGE decisions:

- PASS: all required evidence is present, no FAIL/CRITICAL/unresolved blockers.
- LOOPBACK: failure can be assigned to P3, P4, P5, or P6.
- PARTIAL: loopback limits are exhausted or required real validation is waived.

Use `docs/judge_template.md`.

## Loopback Policy

Loopback repairs design/test/implementation/integration errors. Requirement
changes start a new cycle instead of mutating the current one.

Limits:

- maximum total loopbacks: 5
- maximum same-phase loopbacks: 2
- same phase failed twice: escalate to the nearest upstream phase
- limits exceeded: write a P9 Partial Report

Return mapping:

- Architecture or contract issue -> P3
- Unit test bug or wrong expectation -> P4
- Implementation bug -> P5
- Integration, E2E, environment, or scenario design issue -> P6

Record every loopback in `docs/loopback_log.md`.

## Done Criteria

Work is done only when:

- RTM status is PASS or PARTIAL
- required gates are approved or waived
- real evidence or waiver is logged
- P8 review status is recorded
- JUDGE decision is recorded
- Final Approval Gate is approved or waived
- P9 final or partial report exists
- `project_progress.md` records the outcome
