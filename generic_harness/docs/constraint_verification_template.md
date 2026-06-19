# Constraint Verification Template

Use this during P1 before design or implementation depends on external facts.

## Header

- **Req ID**:
- **Date**:
- **Verifier**:
- **Environment**:

## Checks

| Assumption | Probe / Command | Expected | Actual | Evidence Path | Status |
| --- | --- | --- | --- | --- | --- |

## Decision

- Verified constraints:
- Unverified assumptions:
- Blockers:
- Requirement Gate needed? Yes / No

## Rules

- An unverified external assumption cannot be treated as fact.
- If a required constraint fails, stop before P3 unless the user revises scope or
  approves a gate decision.
- Link this file from `docs/rtm.md`.
