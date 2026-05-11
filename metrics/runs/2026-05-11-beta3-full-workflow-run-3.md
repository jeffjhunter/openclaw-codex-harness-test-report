# Beta 3 Full Workflow Benchmark - Run 3

## Requested Artifact

- Path: `metrics/runs/2026-05-11-beta3-full-workflow-run-3.md`
- Target public repo: `https://github.com/jeffjhunter/openclaw-codex-harness-test-report`
- Task: full workflow benchmark through the live Discord Codex harness path.

## Runtime Evidence

- OpenClaw version: `OpenClaw 2026.5.10-beta.3 (6d7dcd9)`
- Codex plugin version: `@openclaw/codex@2026.5.10-beta.3`
- Provider/model if visible: `openai/gpt-5.5`
- Codex harness path status: OpenClaw session status reported `Execution: direct` and `Runtime: OpenAI Codex`.
- Visible tool count: `208`

## Workflow

- Branch name: `beta3/full-workflow-benchmark-run-3-20260511`
- Commit hash: `ddc45c9a0a167ad581977b70a013d0de14f08987`
- Final PR head hash: `c183d15da17c683854fa13d08935efcedda8a937`
- PR URL: `https://github.com/jeffjhunter/openclaw-codex-harness-test-report/pull/7`
- PR/check status: no checks reported; `statusCheckRollup` was empty
- GitHub deployment/Vercel status: no GitHub deployment reported; Vercel was not checked
- Browser screenshot: captured and verified locally

## Browser Actions Used

Actual OpenClaw browser tool was used. This was not `openclaw browser` shell CLI and not `google-chrome --headless`.

- `openclaw_browser action=open`
- `openclaw_browser action=snapshot`
- `openclaw_browser action=screenshot`

## Timing

- Start time UTC: `2026-05-11T07:00:28.235Z`
- End time UTC: `2026-05-11T07:00:36.987Z`
- Duration seconds: `8.752`

## Token Usage

Token usage was visible only as a session-level status snapshot, not isolated per benchmark run.

- Input: `3.3k in`
- Output: `96 out`
- Cache read: `215k cached / 98% hit`
- Cache write: `0 new`
- Total: not exposed as a single exact per-run total

## Tool Calls

Exact per-run tool call count was not exposed as a runtime metric.

Tools used during this benchmark sequence:

- `exec_command`
- `apply_patch`
- `openclaw_session_status`
- `openclaw_browser`
- `message`

## Error Tracking

- Fallback errors: none observed.
- Timeout errors: none observed.
- Pairing errors: none observed.
- Scope-upgrade errors: none observed.
- Auth errors: none observed.
- Private repo links: none used.
