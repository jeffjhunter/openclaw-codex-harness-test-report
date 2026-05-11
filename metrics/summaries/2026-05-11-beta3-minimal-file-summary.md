# Beta 3 Minimal File Benchmark Summary

Date: 2026-05-11

OpenClaw version: `2026.5.10-beta.3`

Codex plugin version: `@openclaw/codex@2026.5.10-beta.3`

Provider/model: `openai/gpt-5.5`

Harness path: live Discord Codex harness

## Result

Three minimal file benchmark artifacts were created successfully.

| Run | Measured artifact-write duration | Visible tools | Errors |
| --- | ---: | ---: | --- |
| 1 | 0.036s | 208 | None observed |
| 2 | 0.035s | 208 | None observed |
| 3 | 0.036s | 208 | None observed |

Average measured artifact-write duration: `0.0357s`

## Token Snapshot

The harness exposed a session-level status snapshot, not isolated per-run token usage.

Observed snapshot:

- Input: `3.4k in`
- Output: `40 out`
- Cache read: `188k cached / 98% hit`
- Cache write: `0 new`

## Tooling

Exact isolated per-run tool-call counts were not exposed.

Observable tools used during the benchmark sequence:

- `exec_command`
- `openclaw_session_status`
- `apply_patch`
- `message`

## Interpretation

This benchmark confirms that the live Discord Codex harness can complete a tiny file-artifact task repeatedly with no observed fallback, timeout, pairing, scope-upgrade, or auth errors.

This does not yet prove beta 3 is faster or more token efficient than beta 2 because:

- Beta 2 data is historical, not controlled.
- The duration measured here is artifact-write duration, not full end-to-end turn duration.
- Per-run token usage was not isolated by the runtime metadata available to the harness.

Next benchmark: browser task repeated three times.
