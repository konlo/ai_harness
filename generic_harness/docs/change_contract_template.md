# Change Contract Template

Copy this template into `docs/agent_tasks/active/` or a durable contract document
before implementation.

## Contract Header

- **Req ID**:
- **Title**:
- **Owner**:
- **Date**:
- **Risk Level**: Low / Medium / High
- **Current Phase**:
- **Gate Status**: Pending / Approved / Waived / Rejected / Not Required
- **Related RTM Row**:

## Requirement

Describe the user-visible behavior and why it matters.

## Pre-State

- System state:
- Actor / caller:
- Data / environment:
- Existing artifact or reproduction:

## Constraints

- External APIs / services:
- Database / storage:
- Device / simulator / browser:
- Library / tool versions:
- Credentials / permissions:
- Constraint verification file:

## Trigger

- Command / event / user action:
- Input:
- Setup:

## Expected Post-State

- Fields or behavior that must change:
- Fields or behavior that must not change:
- Evidence expected:

## Non-Regression Constraints

- Domain constraints:
- Interface constraints:
- Test constraints:
- External dependency constraints:
- Security / privacy constraints:

## Allowed Implementation Scope

- Allowed files / directories:
- Forbidden files / directories:
- Required review:

## Validation Plan

- Build command:
- Unit / scenario command:
- Real E2E command:
- Artifact path:
- PASS signature:
- FAIL signature:
- Real E2E waiver gate, if any:

## Loopback Plan

If validation fails, classify first:

- Architecture or contract issue -> P3
- Unit test bug or wrong expectation -> P4
- Implementation bug -> P5
- Integration/E2E scenario or environment issue -> P6
- Requirement change -> new cycle

Then update `docs/loopback_log.md` before additional edits.
