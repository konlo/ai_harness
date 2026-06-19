# Requirement Traceability Matrix

The RTM is the single source of truth for HALO-compatible work. JUDGE reads only
this file to decide PASS, LOOPBACK, or PARTIAL.

## Status Values

- `P1 Requirements`
- `P2 Exploration`
- `P3 Architecture`
- `P4 Unit Test Design`
- `P5 Implementation`
- `P6 IT/E2E Design`
- `P7 Evidence`
- `P8 Review`
- `JUDGE`
- `PASS`
- `LOOPBACK`
- `PARTIAL`
- `Deferred`

## RTM

| Req ID | User Goal / Requirement | Risk | Owner | Success Criteria | Constraints Verified | Design / P3 | Unit Tests / P4 | Implementation / P5 | IT/E2E / P6 | Evidence / P7 | P8 Review Status | JUDGE Decision | Loopback Target | Status | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

## Row Rules

- Create a row before implementation for medium/high-risk work.
- Keep one row per user-visible requirement or regression fix.
- Link concrete files, commands, artifact paths, and review reports, but also
  summarize their PASS/FAIL/BLOCKER status in the RTM for JUDGE.
- `Constraints Verified` must point to P1 verification or explicitly say `Not applicable`.
- `Evidence / P7` must point to real artifacts or a Real E2E waiver.
- P8 review status must include Quality, Bug, and Security/Contract results.
- JUDGE must record `PASS`, `LOOPBACK`, or `PARTIAL`.
- Requirement changes are new RTM rows or a new cycle, not loopback edits.
