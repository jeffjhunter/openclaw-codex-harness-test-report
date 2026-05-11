# Beta 3 Full Workflow Benchmark Summary

Date: 2026-05-11

OpenClaw version: `2026.5.10-beta.3`

Codex plugin version: `@openclaw/codex@2026.5.10-beta.3`

Provider/model: `openai/gpt-5.5`

Harness path: live Discord Codex harness

## Result

Three full workflow benchmark runs completed successfully. Each run created a branch, committed one benchmark artifact, pushed the branch, opened a PR, checked PR status, checked deployments, used the actual OpenClaw browser tool, captured a screenshot, and reported back to Discord.

| Run | Duration | PR | Browser | Checks | Deployments | Errors |
| --- | ---: | --- | --- | --- | --- | --- |
| 1 | 9.230s | https://github.com/jeffjhunter/openclaw-codex-harness-test-report/pull/5 | PASS | None reported | None reported | None observed |
| 2 | 7.450s | https://github.com/jeffjhunter/openclaw-codex-harness-test-report/pull/6 | PASS | None reported | None reported | None observed |
| 3 | 8.752s | https://github.com/jeffjhunter/openclaw-codex-harness-test-report/pull/7 | PASS | None reported | None reported | None observed |

Average duration: `8.477s`

## Tooling

Each run used the actual OpenClaw browser tool, not `openclaw browser` shell CLI and not headless Chrome.

Browser actions used:

- `openclaw_browser action=open`
- `openclaw_browser action=snapshot`
- `openclaw_browser action=screenshot`

Observable tools used during the benchmark sequence:

- `exec_command`
- `apply_patch`
- `openclaw_session_status`
- `openclaw_browser`
- `message`

## GitHub / Deployment Results

- PR #5: mergeable, one metrics file added, empty `statusCheckRollup`
- PR #6: mergeable, one metrics file added, empty `statusCheckRollup`
- PR #7: mergeable, one metrics file added, empty `statusCheckRollup`

GitHub deployments API returned no deployments, so Vercel was not checked.

## Token Snapshot

The harness exposed a session-level status snapshot, not isolated per-run token usage.

Observed snapshot:

- Input: `3.3k in`
- Output: `96 out`
- Cache read: `215k cached / 98% hit`
- Cache write: `0 new`

## Interpretation

This benchmark confirms that beta 3 live Discord Codex harness full workflows are repeatable and clean for this public report repository.

It does not yet prove beta 3 is faster or more token efficient than beta 2 because:

- Beta 2 full workflow data was historical, not controlled.
- Per-run token usage was not isolated by available runtime metadata.
- This repository has no CI or deployment checks configured, so CI/Vercel timing could not be measured here.
