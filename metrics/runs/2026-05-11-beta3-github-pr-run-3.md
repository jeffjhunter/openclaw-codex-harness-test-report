# Beta 3 GitHub PR Benchmark - Run 3

## Requested Artifact

- Path: `metrics/runs/2026-05-11-beta3-github-pr-run-3.md`
- Target public repo: `https://github.com/jeffjhunter/openclaw-codex-harness-test-report`
- Task: GitHub PR benchmark through the live Discord Codex harness path.

## Runtime Evidence

- OpenClaw version: `OpenClaw 2026.5.10-beta.3 (6d7dcd9)`
- Codex plugin version: `@openclaw/codex@2026.5.10-beta.3`
- Provider/model if visible: `openai/gpt-5.5`
- Codex harness path status: OpenClaw session status reported `Execution: direct` and `Runtime: OpenAI Codex`.
- Visible tool count: `208`

## GitHub Workflow

- Branch name: `beta3/github-pr-benchmark-run-3-20260511`
- Initial artifact commit hash: `987442ccf60da158714f9d44742849e0c9fa5bf7`
- Final PR head hash: `e1f0cca0a148de8c52d7d99fd79e01e9853eefab`
- PR URL: `https://github.com/jeffjhunter/openclaw-codex-harness-test-report/pull/4`
- PR/check status: no checks reported; `statusCheckRollup` was empty
- GitHub deployment reported: no
- Vercel checked: no, because GitHub reported no deployment

## Timing

- Start time UTC: `2026-05-11T06:45:22.912Z`
- End time UTC: `2026-05-11T06:45:29.400Z`
- Duration seconds: `6.488`

## Token Usage

Token usage was visible only as a session-level status snapshot, not isolated per PR benchmark run.

- Input: `3.4k in`
- Output: `47 out`
- Cache read: `201k cached / 98% hit`
- Cache write: `0 new`
- Total: not exposed as a single exact per-run total

## Tool Calls

Exact per-run tool call count was not exposed as a runtime metric.

Tools used during this benchmark sequence:

- `exec_command`
- `apply_patch`
- `openclaw_session_status`
- `message`

## Error Tracking

- Fallback errors: none observed.
- Timeout errors: none observed.
- Pairing errors: none observed.
- Scope-upgrade errors: none observed.
- Auth errors: none observed.
- Browser usage: intentionally not used.
- Private repo links: none used.
