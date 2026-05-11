# Beta 2 Historical Baseline

Date extracted: 2026-05-11

OpenClaw version: `2026.5.10-beta.2`

Model: `gpt-5.5`

Provider: `openai`

## Summary

The beta 2 data below comes from existing trajectory/session files, not from a controlled benchmark suite. It is useful for rough context but should not be treated as a definitive performance baseline.

Most beta 2 runs were smoke or diagnostic prompts. They do provide token usage and timing for several small harness turns, plus separate evidence that browser and full workflow tasks worked.

## Extracted Historical Runs

| Session | Approx duration | Input | Output | Cache read | Total | Notes |
| --- | ---: | ---: | ---: | ---: | ---: | --- |
| `codex-harness-smoke-2026-05-11-final` | 2.1s | 17,868 | 15 | 3,456 | 21,339 | Small final smoke turn. |
| `codex-harness-smoke-2026-05-11` run 1 | 12.7s | 12,867 | 100 | 6,528 | 19,495 | Smoke turn. |
| `codex-harness-smoke-2026-05-11` run 2 | 3.6s | 657 | 133 | 18,816 | 19,606 | Follow-up smoke turn. |
| `thorough-openai-exact-20260511` | 5.9s | 17,863 | 21 | 3,456 | 21,340 | Model/provider check. |
| `thorough-tooluse-20260511` | 5.2s | 632 | 8 | 20,864 | 21,504 | Tool-use diagnostic. |
| `thorough-command-status-20260511` | 8.0s | 1,220 | 103 | 20,864 | 22,187 | Status command diagnostic. |
| `thorough-command-codex-models-20260511` | 6.2s | 17,852 | 167 | 3,456 | 21,475 | Codex models diagnostic. |
| `thorough-command-codex-status-20260511` | 13.7s | 17,852 | 98 | 3,456 | 21,406 | Codex status diagnostic. |
| `thorough-unknown-slash-20260511` | 3.4s | 450 | 52 | 20,864 | 21,366 | Unknown command handling. |

## Historical Beta 2 Workflow Evidence

Additional beta 2 evidence exists for larger workflows, but not all fields are available in a benchmark-friendly format:

- Brand guide real-world task: shell-heavy workflow with `bash=64`, `apply_patch=7`, and no browser tool calls in the original task.
- Browser follow-up test: actual browser tool path confirmed with 15 browser tool calls.
- Full GitHub/CI/Vercel/Discord audit: passed GitHub and CI checks; Vercel preview existed but HTTP verification returned `401`.

## Interpretation

This is enough to say:

- Beta 2 harness telemetry exists.
- Beta 2 small diagnostic turns often landed around roughly 19k-22k total tokens.
- Beta 2 had duplicate/searchable dynamic-tool behavior and did not include beta 3 code mode.

This is not enough to say:

- Beta 3 is definitively faster than beta 2.
- Beta 3 uses fewer tokens than beta 2 for the same task.

Those claims need controlled beta 3 benchmark runs and comparable beta 2 historical matching.
