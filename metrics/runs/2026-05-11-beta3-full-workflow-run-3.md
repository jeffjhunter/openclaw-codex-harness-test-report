# Beta 3 Full Workflow Benchmark - Run 3

## Requested Artifact

- Path: `metrics/runs/2026-05-11-beta3-full-workflow-run-3.md`
- Target public repo: `https://github.com/jeffjhunter/openclaw-codex-harness-test-report`
- Task: full workflow benchmark through the live Discord Codex harness path.

## Runtime Evidence

- OpenClaw version: `OpenClaw 2026.5.10-beta.3 (6d7dcd9)`
- Codex plugin version: `@openclaw/codex@2026.5.10-beta.3`
- Provider/model if visible: `openai/gpt-5.5`
- Codex harness path status: Active: session status reports Execution: direct and Runtime: OpenAI Codex.
- Visible tool count: `208`

## Workflow

- Branch name: `beta3/full-workflow-benchmark-run-3-20260511`
- Commit hash: `ddc45c9a0a167ad581977b70a013d0de14f08987`
- PR URL: `https://github.com/jeffjhunter/openclaw-codex-harness-test-report/pull/7`
- PR/check status: `no checks reported on the 'beta3/full-workflow-benchmark-run-3-20260511' branch`
- GitHub deployment/Vercel status: `No GitHub deployment reported; Vercel was not checked.`
- Browser screenshot path: `/home/aerofarmai/.openclaw/media/browser/00beb53c-761f-4011-9f18-978535518b3d.png`

## Browser Actions Used

Actual OpenClaw browser tool was required and used. This was not `openclaw browser` shell CLI and not `google-chrome --headless`.

- `openclaw_browser action=open`
- `openclaw_browser action=snapshot`
- `openclaw_browser action=screenshot`

## Timing

- Start time UTC: `2026-05-11T07:00:28.235Z`
- End time UTC: `2026-05-11T07:00:36.987Z`
- Duration seconds: `8.752`

## Token Usage

Token usage is visible only as a session-level status snapshot, not isolated per benchmark run.

- Input: `3.3k in (session status snapshot before full workflow benchmark runs)`
- Output: `96 out (session status snapshot before full workflow benchmark runs)`
- Cache read: `215k cached / 98% hit (session status snapshot before full workflow benchmark runs)`
- Cache write: `0 new (session status snapshot before full workflow benchmark runs)`
- Total: `not exposed as a single exact total; visible snapshot was 3.3k in / 96 out plus 215k cached`

## Tool Calls

Exact per-run tool call count is not exposed as a runtime metric.

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

## Metadata Update

This file was updated after PR creation and browser capture to record PR/check/deployment/screenshot evidence. The commit hash above is the initial artifact commit created for the run.

