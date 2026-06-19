# Gate Checklist

Gate status values:

- `Pending`
- `Approved`
- `Waived`
- `Rejected`

| Gate ID | Req ID | Gate | Phase | Decision | Decider | Date | Evidence / Contract | Residual Risk | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

## Required Gates

- **Requirement Gate**: after P1 when requirement interpretation, scope, or
  constraints may be wrong.
- **Architecture Gate**: after P3 when design direction is expensive to reverse.
- **Real E2E Waiver Gate**: before skipping required real validation.
- **Final Approval Gate**: after JUDGE returns PASS or PARTIAL and before P9.
- **Contract Change Gate**: before changing public state, API, protocol, UI, data,
  or security contracts.

## Rules

- A missing gate is not approval.
- A waived gate must include residual risk.
- A rejected gate stops work until the phase output is revised.
- Gate decisions are human direction checkpoints, not substitutes for evidence.
