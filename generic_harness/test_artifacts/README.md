# Test Artifacts

Store runtime validation evidence here.

Recommended structure:

```text
test_artifacts/<suite>/<scenario>/<run_id>/
  summary.md
  manifest.json
  logs/
  timeline/
  snapshots/
  screenshots/
  replay/
```

Rules:

- Keep artifacts reproducible.
- Prefer summaries plus raw logs/events.
- Record real environment details for E2E evidence.
- Mark mocked runs explicitly; mocked E2E is not real E2E PASS.
- Do not commit large artifacts unless they are intentional baselines.
- Link important artifacts from `docs/e2e_evidence_log.md` and `docs/rtm.md`.
