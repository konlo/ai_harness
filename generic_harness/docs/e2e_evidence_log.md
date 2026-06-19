# E2E Evidence Log

| Evidence ID | Req ID | Phase | Scenario / Command | Environment | Real E2E? | Mocked? | Artifact Manifest | PASS Signature | Reviewer | Date | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

## Evidence Rules

- Prefer artifact paths over prose.
- Record environment details when behavior crosses process, network, UI, model,
  service, device, or external dependency boundaries.
- `Real E2E?` must be `Yes`, `No`, or `Not applicable`.
- `Mocked?` must be `No` for real E2E PASS.
- Mocked E2E cannot prove PASS for external-boundary behavior.
- Missing artifacts are inconclusive, not PASS.
- If validation fails, update `docs/loopback_log.md`.
- If real E2E is skipped, link a Real E2E Waiver Gate.
