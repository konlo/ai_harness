# AI Harness

This repository stores two related artifacts:

1. A local archive of FREEDOBY's AI Agent / HALO Workflow article series.
2. A reusable HALO-compatible generic harness template for AI-assisted software work.

## Agent Instruction Priority

`CLAUDE.md` is the primary local behavior guide for this repository. Agents
should read it first, then use `AGENTS.md` for priority routing and the
`generic_harness/` runbooks for HALO-specific work.

## Contents

### `doc/`

Local copy of the six-part FREEDOBY series used as the conceptual source for the
harness design.

- `series-1.html` / `series-1.txt`: AI Agent's clear limits.
- `series-2.html` / `series-2.txt`: why those limits happen.
- `series-3.html` / `series-3.txt`: Prompt -> Context -> Harness engineering.
- `series-4.html` / `series-4.txt`: divide-and-conquer phase design.
- `series-5.html` / `series-5.txt`: judgment, responsibility, and iteration.
- `series-6.html` / `series-6.txt`: HALO Workflow as a concrete structure.
- `images/`: local image assets used by the archived HTML pages.
- `css/style.css`: local stylesheet used by the archived HTML pages.
- `manifest.json`: source URLs, titles, and saved file metadata.

The HTML files are adjusted to use local images and CSS, so they can be opened
offline from this repository.

### `generic_harness/`

Reusable HALO-compatible project template.

The harness is built around:

- **9 Phase Workflow**: `P1 -> P2 -> P3 -> P4 -> P5 -> P6 -> P7 -> P8 -> JUDGE -> Final Approval Gate -> P9`
- **File = Interface**: phase handoff happens through files, not chat history.
- **RTM as Single Source of Truth**: requirements, design, tests, implementation,
  evidence, reviews, JUDGE decisions, and loopbacks are tracked in one matrix.
- **P8 Review x3**: Quality, Bug, and Security/Contract review perspectives.
- **RTM-only JUDGE**: JUDGE reads only `docs/rtm.md`.
- **Loopback Policy**: failures return to P3/P4/P5/P6 with loop limits.
- **Constraint Verification**: external assumptions are verified during P1.
- **Real E2E Policy**: mocked E2E cannot prove PASS for real boundary behavior.

Key files:

- `generic_harness/README.md`: harness overview and start order.
- `generic_harness/AGENTS_TEMPLATE.md`: project-level agent instructions.
- `generic_harness/docs/runbooks/halo_operating_flow.md`: main HALO operating rules.
- `generic_harness/docs/runbooks/orchestrator_agent_flow.md`: orchestrator rules.
- `generic_harness/docs/rtm.md`: requirement traceability matrix.
- `generic_harness/docs/phase_templates/`: P1-P9 phase templates.
- `generic_harness/docs/review_templates/`: P8 review templates.
- `generic_harness/docs/judge_template.md`: RTM-only JUDGE template.
- `generic_harness/docs/final_report_template.md`: P9 final/partial report template.

## Intended Use

Use `doc/` to inspect the source ideas behind the harness.

Use `generic_harness/` by copying it into a new project, replacing placeholders in
`AGENTS_TEMPLATE.md`, then starting work from
`docs/orchestrator_prompt_template.md`.

The harness is designed to prevent common AI-agent failure modes:

- blind context
- context rot
- untracked decisions
- mock-only success
- unclear human approval points
- repeated unclassified repair loops
