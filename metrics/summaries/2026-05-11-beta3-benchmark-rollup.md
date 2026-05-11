# Beta 3 Benchmark Rollup

Date: 2026-05-11

OpenClaw version: `2026.5.10-beta.3`

Codex plugin version: `@openclaw/codex@2026.5.10-beta.3`

Provider/model: `openai/gpt-5.5`

Harness path: live Discord Codex harness

## Benchmark Summary

| Task | Runs | Average measured duration | Visible tools | Result |
| --- | ---: | ---: | ---: | --- |
| Minimal file artifact | 3 | 0.0357s | 208 | PASS |
| Browser task | 3 | 2.221s | 208 | PASS |
| GitHub PR task | 3 | 6.575s | 208 | PASS |
| Full workflow task | 3 | 8.477s | 208 | PASS |

Across all benchmark groups:

- No fallback errors observed.
- No timeout errors observed.
- No pairing errors observed.
- No scope-upgrade errors observed in the live Discord Codex harness path.
- No auth errors observed.
- Dynamic/Codex tool surface remained visible with 208 tools.

## Token Observability

The runtime exposed session-level token snapshots, but not isolated per-run token usage.

Observed snapshots across benchmark groups:

| Task group | Input | Output | Cache read | Cache write |
| --- | ---: | ---: | ---: | ---: |
| Minimal file | 3.4k | 40 | 188k / 98% hit | 0 new |
| Browser | 3.6k | 38 | 193k / 98% hit | 0 new |
| GitHub PR | 3.4k | 47 | 201k / 98% hit | 0 new |
| Full workflow | 3.3k | 96 | 215k / 98% hit | 0 new |

## Current Conclusion

Beta 3 Codex code-mode testing shows repeatable clean execution across file, browser, GitHub PR, and full workflow tasks through the live Discord Codex harness path.

This supports the architectural and behavioral parts of the beta 3 claim:

- Codex beta 3 code-mode source flags are present.
- Dynamic tools remain discoverable through the Codex tool surface.
- Workflows behave like real Codex coding sessions.
- Live Discord Codex harness runs avoid the CLI scope-upgrade issue.

It does not yet prove beta 3 is faster or more token efficient than beta 2 because:

- Beta 2 measurements are historical and not controlled.
- The measured beta 3 durations are task-phase durations, not full end-to-end user-visible latency.
- Per-run token usage is not exposed as isolated runtime metadata.

## Recommended Follow-Up

Ask OpenClaw developers whether Codex harness can expose per-turn metrics for:

- full turn wall-clock duration
- input tokens
- output tokens
- cache read/write tokens
- total tokens
- tool call count
- visible tool count
- code-mode/code-mode-only state

Those metrics would make beta-to-beta performance validation much stronger.
