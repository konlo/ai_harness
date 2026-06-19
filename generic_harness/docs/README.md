# Docs Layout

This folder stores harness controls, active phase outputs, archived prompts,
reports, reviews, and runbooks.

## Required Operating Flow

Medium/high-risk work must follow:

```text
P1 -> P2 -> P3 -> P4 -> P5 -> P6 -> P7 -> P8 -> JUDGE -> Final Approval Gate -> P9
```

All phase handoff happens through files. The RTM is the single source of truth.

## Required Operating Files

- `docs/harness_file_index.md`: role-based file map.
- `docs/runbooks/orchestrator_agent_flow.md`: orchestrator state machine and delegation rules.
- `docs/runbooks/halo_operating_flow.md`: mandatory HALO phase loop and done criteria.
- `docs/orchestrator_prompt_template.md`: prompt for starting an orchestrator session.
- `docs/orchestrator_board.md`: queue, decisions, open questions, and handoff notes.
- `docs/rtm.md`: requirement traceability matrix.
- `docs/gate_checklist.md`: approval and waiver log.
- `docs/e2e_evidence_log.md`: artifact-backed evidence log.
- `docs/loopback_log.md`: failure classification and return decision log.
- `docs/judge_template.md`: RTM-only JUDGE decision template; JUDGE is not a phase.
- `docs/final_report_template.md`: P9 final or partial report template.
- `docs/constraint_verification_template.md`: P1 external assumption checks.

## Directories

- `docs/phase_templates/`: P1-P9 phase checklist templates.
- `docs/review_templates/`: P8 review templates.
- `docs/agent_tasks/active/`: active contracts, phase outputs, and bounded prompts.
- `docs/agent_tasks/archive/`: completed task prompts and handoff notes.
- `docs/reports/`: final reports, partial reports, and investigations.
- `docs/runbooks/`: repeatable operating procedures.
- `docs/skills/`: copied or project-specific skill instructions.
