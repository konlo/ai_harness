# Loopback Log

| Loopback ID | Req ID | Judge Decision | Failed Evidence / Review | First Bad Transition | Classification | Return Phase | Same-Phase Count | Total Loop Count | Escalation | Decision | Date | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

## Classifications

- `Arch Issue` -> P3
- `Unit Test Bug` -> P4
- `Impl Bug` -> P5
- `Integration / E2E Design` -> P6
- `Environment / Constraint` -> P1 or Gate
- `Requirement Change` -> new cycle, not loopback

## Loopback Rules

- Record the first failing transition, not just the final error.
- Do not patch a second layer until the failure is classified.
- Maximum total loopbacks: 5.
- Maximum same-phase loopbacks: 2.
- If the same phase fails twice, escalate to the nearest upstream phase.
- If limits are exceeded, write a P9 Partial Report.
- If environment reset fixes the issue, classify it as stale environment unless
  artifacts prove a code fix.
