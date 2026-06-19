# Generic AI Harness

Reusable HALO-compatible harness for starting new AI-assisted projects.

HALO means:

```text
Harness · Agentic · Loopback · Orchestration
```

Use this package to make AI work traceable, recoverable, resistant to
mock-only success, and restartable from files instead of chat history.

## Core Workflow

HALO-compatible work uses one shared RTM and nine phases:

```text
P1 Requirements + Constraint Verification
P2 Exploration
P3 Architecture
P4 Unit Test Design
P5 Implementation
P6 Integration / E2E Test Design
P7 Test Execution + Evidence
P8 Code Review x3
JUDGE -> Final Approval Gate -> P9 Final / Partial Report
```

All medium/high-risk work must update the RTM, pass required gates, produce
artifact-backed evidence, and use loopback instead of ad hoc repair.

## Start Order

1. Copy this folder into a new project.
2. Rename project-specific placeholders in `AGENTS_TEMPLATE.md`.
3. Start an orchestrator session with `docs/orchestrator_prompt_template.md`.
4. Create the first RTM row in `docs/rtm.md`.
5. Run P1 constraint verification for external assumptions.
6. Create phase outputs under `docs/agent_tasks/active/`.
7. Record gates in `docs/gate_checklist.md`.
8. Record real validation artifacts in `docs/e2e_evidence_log.md`.
9. Use `docs/judge_template.md` before declaring PASS or PARTIAL.
10. Close with a P9 report and an entry in `project_progress.md`.

## File = Interface

Phase handoff happens through files, not hidden chat context.

- Each phase reads only the RTM and the files named by the previous phase.
- Each phase writes a durable output file and updates the RTM.
- A new session must be able to resume from the RTM plus phase outputs.
- `.workflow/` is reserved for temporary checkpoints and should be gitignored in
  real projects unless a project intentionally keeps those artifacts.

## Files

- `AGENTS_TEMPLATE.md`: project-level agent instructions template.
- `docs/runbooks/orchestrator_agent_flow.md`: orchestrator operating rules.
- `docs/runbooks/halo_operating_flow.md`: mandatory HALO work loop.
- `docs/phase_templates/`: P1-P9 phase checklist templates.
- `docs/review_templates/`: P8 Quality, Bug, and Security/Contract reviews.
- `docs/judge_template.md`: RTM-only JUDGE decision template; JUDGE is not a phase.
- `docs/final_report_template.md`: P9 final or partial report template.
- `docs/constraint_verification_template.md`: P1 external-assumption checks.
- `docs/rtm.md`: requirement traceability matrix and single source of truth.
- `docs/gate_checklist.md`: approval and waiver log.
- `docs/e2e_evidence_log.md`: artifact-backed evidence log.
- `docs/loopback_log.md`: failure recovery and loop count log.
- `test_artifacts/README.md`: artifact policy.
