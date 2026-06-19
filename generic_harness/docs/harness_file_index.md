# Harness File Index

Role-based index for a generic HALO-compatible AI harness.

## Start Here

| File | Role |
| --- | --- |
| `AGENTS_TEMPLATE.md` | Project-level agent rules template. |
| `README.md` | Package overview and start order. |
| `docs/README.md` | Docs layout and required operating files. |
| `docs/harness_file_index.md` | This index. |

## Orchestrator Layer

| File | Role |
| --- | --- |
| `docs/runbooks/orchestrator_agent_flow.md` | Orchestrator mission, phase loop, delegation rules, and stop conditions. |
| `docs/orchestrator_prompt_template.md` | Prompt for starting an orchestrator session. |
| `docs/orchestrator_board.md` | Queue, decisions, open questions, and handoff notes. |

## HALO Operating Loop

| File | Role |
| --- | --- |
| `docs/runbooks/halo_operating_flow.md` | 9-phase workflow, File = Interface, RTM-only JUDGE, Real E2E, and loopback policy. |
| `docs/rtm.md` | Single source of truth for requirements, design, tests, implementation, evidence, review, JUDGE. |
| `docs/change_contract_template.md` | Contract template before implementation. |
| `docs/gate_checklist.md` | Approval and waiver log. |
| `docs/e2e_evidence_log.md` | Artifact-backed real validation log. |
| `docs/loopback_log.md` | Failure classification, loop counts, escalation, and return decision log. |
| `docs/judge_template.md` | RTM-only JUDGE decision template; JUDGE is separate from the 9 phases. |
| `docs/final_report_template.md` | P9 final or partial report template. |
| `docs/constraint_verification_template.md` | P1 external constraint verification template. |
| `project_progress.md` | Request-level progress log. |

## Templates

| Directory | Role |
| --- | --- |
| `docs/phase_templates/` | P1-P9 phase output checklists. |
| `docs/review_templates/` | P8 Quality, Bug, and Security/Contract reviews. |
| `docs/agent_tasks/active/` | Active phase outputs, contracts, and bounded prompts. |
| `docs/agent_tasks/archive/` | Completed phase outputs and handoff notes. |
| `docs/reports/` | P9 reports and investigations. |

## Runtime Artifacts

- `test_artifacts/`: real validation evidence.
- `.workflow/`: temporary checkpoints; gitignore in real projects unless
  intentionally preserved.
