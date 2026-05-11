# Beta 3 Browser Benchmark Summary

Date: 2026-05-11

OpenClaw version: `2026.5.10-beta.3`

Codex plugin version: `@openclaw/codex@2026.5.10-beta.3`

Provider/model: `openai/gpt-5.5`

Harness path: live Discord Codex harness

## Result

Three browser benchmark artifacts were created successfully. Each run used the actual OpenClaw browser tool, not the browser shell CLI and not headless Chrome.

| Run | Duration | Browser actions | Visible tools | Errors |
| --- | ---: | ---: | ---: | --- |
| 1 | 1.950s | 4 | 208 | None observed |
| 2 | 2.391s | 4 | 208 | None observed |
| 3 | 2.321s | 4 | 208 | None observed |

Average duration: `2.221s`

## Browser Actions

Each run used:

- `openclaw_browser action=open`
- `openclaw_browser action=snapshot`
- `openclaw_browser action=act` with `evaluate`
- `openclaw_browser action=screenshot`

## Browser Observations

Each run loaded the public report repository successfully.

- Repository: `jeffjhunter/openclaw-codex-harness-test-report`
- Visibility: `Public`
- Screenshots: captured and verified locally as valid PNG files

## Token Snapshot

The harness exposed a session-level status snapshot, not isolated per-run token usage.

Observed snapshot:

- Input: `3.6k in`
- Output: `38 out`
- Cache read: `193k cached / 98% hit`
- Cache write: `0 new`

## Interpretation

This benchmark confirms that beta 3 live Discord Codex harness browser usage is repeatable and clean for the public report repository.

It does not yet prove beta 3 is faster or more token efficient than beta 2 because:

- Beta 2 browser task data was historical, not controlled.
- Per-run token usage was not isolated by available runtime metadata.
- This measures browser tool operation duration, not full end-to-end conversation latency.

Next benchmark: GitHub PR task repeated three times.
