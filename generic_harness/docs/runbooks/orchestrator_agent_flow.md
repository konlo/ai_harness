# Orchestrator Agent Flow

The orchestrator controls the HALO-compatible harness. It does not replace
human judgment at gates.

```text
Main Agent: P1 -> P2 -> P3 -> P4 -> P5 -> P6 -> P7 -> coordinate P8/JUDGE -> Final Approval Gate -> P9
Subagents:  P8 Quality/Bug/Security reviews, JUDGE RTM-only decision
```

## Mission

The orchestrator:

- classifies request risk
- creates or updates RTM rows
- runs the 9-phase workflow for medium/high-risk work
- enforces File = Interface handoff
- records gates, evidence, reviews, judge decisions, and loopbacks
- stops when human judgment or real validation is required

## Required Inputs

Read as needed:

- `docs/runbooks/halo_operating_flow.md`
- `docs/rtm.md`
- `docs/gate_checklist.md`
- `docs/e2e_evidence_log.md`
- `docs/loopback_log.md`
- `docs/orchestrator_board.md`
- current phase output under `docs/agent_tasks/active/`
- project contract documents relevant to the request

## Risk Levels

Low:

- documentation-only changes
- narrow copy edits
- non-behavioral cleanup

Medium:

- test harness changes
- local behavior changes covered by scenarios
- UI/API changes with limited blast radius

High:

- protocol or public contract changes
- data/state migration
- security, privacy, payment, legal, or production infrastructure
- external dependency behavior
- changes that can produce mock-only success

Medium/high-risk work requires RTM, phase outputs, gates as applicable,
artifact-backed evidence, P8 review, and JUDGE.

## Main Agent First

The main agent should execute P1-P7 and P9 in one coherent workflow when
possible. This preserves decision consistency.

Use files to avoid context rot:

- write phase outputs
- link them from RTM
- read only the files needed for the next phase

## Delegation Rules

Delegate only where independence or multiple perspectives matter:

- P8 Quality review: one bounded review prompt
- P8 Bug review: one bounded review prompt
- P8 Security/Contract review: one bounded review prompt
- JUDGE: one RTM-only decision prompt

Do not delegate ordinary phase work unless the task is too large for the main
agent and the handoff file explicitly defines inputs, outputs, forbidden files,
validation command, and RTM fields.

## Owner Lanes

Customize these lanes per project.

| Work Type | Owner Lane |
| --- | --- |
| Domain logic / state / rules | Core |
| API / backend / integration | Backend |
| UI / client / user interaction | UI |
| Test / runner / artifact / validation | Test |
| Planning / gates / delegation / loopback | Orchestrator |
| RTM-only final decision | JUDGE |

## Operating Loop

1. Triage request and risk.
2. Create or update RTM row.
3. Run P1 constraint verification.
4. Record Requirement Gate when needed.
5. Run P2 and P3, then record Architecture Gate when needed.
6. Run P4-P7 with real evidence or waiver.
7. Run P8 review x3 and update RTM.
8. Run JUDGE from `docs/rtm.md` only.
9. If JUDGE returns LOOPBACK, update loopback log and return to P3/P4/P5/P6.
10. If JUDGE returns PASS or PARTIAL, record Final Approval Gate.
11. After Final Approval Gate is approved or waived, write P9 report and progress log.

## Stop Conditions

Stop and ask the user when:

- a required gate is pending or rejected
- external constraints cannot be verified
- required real E2E cannot run and no waiver exists
- owner lane or requirement intent is ambiguous
- loopback limits are reached
- same phase failed twice and escalation is unclear
- next action is destructive or broad refactor
