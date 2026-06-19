# Orchestrator Board

Tracks orchestrator-level queue, gates, phase state, and decisions.

## Current State

- **Date**:
- **Mode**:
- **Active Req ID**:
- **Current Phase**:
- **Current State**:
- **Loopback Count**:

## Queue

| Req ID | Request | Risk | Owner Lane | Current Phase | Current State | Next Action |
| --- | --- | --- | --- | --- | --- | --- |

## Gate Queue

| Gate ID | Req ID | Gate | Phase | Pending Decision | Blocked Phase |
| --- | --- | --- | --- | --- | --- |

## Decision Log

| Date | Req ID | Phase | Decision | Reason | Evidence |
| --- | --- | --- | --- | --- | --- |

## Open Contract Questions

- None.

## Handoff Notes

- Start future orchestrator sessions from `docs/orchestrator_prompt_template.md`.
- Resume active work from `docs/rtm.md` and linked phase outputs.
