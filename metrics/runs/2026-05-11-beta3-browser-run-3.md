# Beta 3 Browser Benchmark - Run 3

## Requested Artifact

- Path: `metrics/runs/2026-05-11-beta3-browser-run-3.md`
- Target: `https://github.com/jeffjhunter/openclaw-codex-harness-test-report`
- Task: browser benchmark through the live Discord Codex harness path.

## Runtime Evidence

- OpenClaw version: `OpenClaw 2026.5.10-beta.3 (6d7dcd9)`
- Codex plugin version: `@openclaw/codex@2026.5.10-beta.3`
- Provider/model if visible: `openai/gpt-5.5`
- Codex harness path status: OpenClaw session status reported `Execution: direct` and `Runtime: OpenAI Codex`.
- Visible tool count: `208`

## Timing

- Start time UTC: `2026-05-11T06:31:38.390Z`
- End time UTC: `2026-05-11T06:31:40.711Z`
- Duration seconds: `2.321`

## Browser Actions Used

Actual OpenClaw browser tool calls were used. This was not `openclaw browser` shell CLI and not `google-chrome --headless`.

- `openclaw_browser action=open`
- `openclaw_browser action=snapshot`
- `openclaw_browser action=act` with `evaluate`
- `openclaw_browser action=screenshot`

## Browser Observations

- Page title: `GitHub - jeffjhunter/openclaw-codex-harness-test-report: Sanitized OpenClaw Codex harness beta test reports · GitHub`
- Repository heading: `jeffjhunter/openclaw-codex-harness-test-report`
- Repository visibility: `Public`
- Screenshot: captured and verified locally

## Token Usage

Token usage was visible only as a session-level status snapshot, not isolated per browser run.

- Input: `3.6k in`
- Output: `38 out`
- Cache read: `193k cached / 98% hit`
- Cache write: `0 new`
- Total: not exposed as a single exact per-run total

## Tool Calls

- Observed browser action count for this run: `4`
- Exact total per-run tool call count was not exposed as a runtime metric.

Tools used during the benchmark sequence:

- `openclaw_browser`
- `exec_command`
- `openclaw_session_status`
- `apply_patch`
- `message`

## Error Tracking

- Fallback errors: none observed.
- Timeout errors: none observed.
- Pairing errors: none observed.
- Scope-upgrade errors: none observed.
- Auth errors: none observed.
- No branch created.
- No PR opened.
- No private repo links used.
