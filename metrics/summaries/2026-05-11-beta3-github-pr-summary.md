# Beta 3 GitHub PR Benchmark Summary

Date: 2026-05-11

OpenClaw version: `2026.5.10-beta.3`

Codex plugin version: `@openclaw/codex@2026.5.10-beta.3`

Provider/model: `openai/gpt-5.5`

Harness path: live Discord Codex harness

## Result

Three GitHub PR benchmark runs completed successfully. Each run created a branch, committed one benchmark artifact, pushed the branch, opened a PR, and checked PR status.

| Run | Duration | PR | Checks | Deployments | Errors |
| --- | ---: | --- | --- | --- | --- |
| 1 | 6.807s | https://github.com/jeffjhunter/openclaw-codex-harness-test-report/pull/2 | None reported | None reported | None observed |
| 2 | 6.429s | https://github.com/jeffjhunter/openclaw-codex-harness-test-report/pull/3 | None reported | None reported | None observed |
| 3 | 6.488s | https://github.com/jeffjhunter/openclaw-codex-harness-test-report/pull/4 | None reported | None reported | None observed |

Average duration: `6.575s`

## GitHub Results

- PR #2: mergeable, one metrics file added, empty `statusCheckRollup`
- PR #3: mergeable, one metrics file added, empty `statusCheckRollup`
- PR #4: mergeable, one metrics file added, empty `statusCheckRollup`

GitHub deployments API returned no deployments, so Vercel was not checked.

## Token Snapshot

The harness exposed a session-level status snapshot, not isolated per-run token usage.

Observed snapshot:

- Input: `3.4k in`
- Output: `47 out`
- Cache read: `201k cached / 98% hit`
- Cache write: `0 new`

## Tooling

Exact isolated per-run tool-call counts were not exposed.

Observable tools used during the benchmark sequence:

- `exec_command`
- `apply_patch`
- `openclaw_session_status`
- `message`

## Interpretation

This benchmark confirms that beta 3 live Discord Codex harness GitHub PR workflows are repeatable and clean for this public report repository.

It does not yet prove beta 3 is faster or more token efficient than beta 2 because:

- Beta 2 GitHub PR benchmark data was historical, not controlled.
- Per-run token usage was not isolated by available runtime metadata.
- This repository has no CI or deployment checks configured, so CI/Vercel timing could not be measured here.

Next benchmark: full workflow task repeated three times.
