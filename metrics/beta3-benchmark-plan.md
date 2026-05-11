# Beta 3 Benchmark Plan

Date: 2026-05-11

OpenClaw version under test: `2026.5.10-beta.3`

## Objective

Measure whether beta 3 Codex code mode is faster and more token efficient in practice for Codex harness threads.

Developer feedback: code mode is experimental, and the current benchmark should focus on Codex because code mode is default there. CLI scope-upgrade behavior is a separate research item and should not be mixed into the Codex performance benchmark.

## Test Protocol

Run each benchmark task three times through the live Discord Codex harness path.

Each run should use:

- Same public repo: `jeffjhunter/openclaw-codex-harness-test-report`
- Same model/provider
- Codex harness only
- Fresh session when possible
- Same prompt text
- No private repo links
- No unrelated file changes

## Run Record Schema

Record this for every run:

```text
task_name:
run_number:
openclaw_version:
codex_plugin_version:
channel:
start_time_utc:
end_time_utc:
duration_seconds:
provider:
model:
agent_harness_id:
transport:
fallback_used:
input_tokens:
output_tokens:
cache_read_tokens:
cache_write_tokens:
total_tokens:
tool_call_count:
tools_used:
visible_tool_count:
errors:
artifact_path:
```

## Benchmark Prompts

### 1. Minimal File Task

```text
Beta 3 performance benchmark: minimal file task.

Create a fresh benchmark artifact under `metrics/runs/`.
Write one small Markdown file containing OpenClaw version, Codex plugin version, current model/provider if visible, visible tool count if available, and this task's start/end time.

At the end, report:
- duration if measurable
- token usage if available
- tool call count if available
- any fallback, timeout, pairing, scope-upgrade, or auth errors

Do not modify unrelated files.
```

### 2. Browser Task

```text
Beta 3 performance benchmark: browser task.

Use the actual OpenClaw browser tool, not shell CLI and not headless Chrome.

Open:
https://github.com/jeffjhunter/openclaw-codex-harness-test-report

Take a snapshot and screenshot. Record title/H1/repo visibility if visible.
Write one benchmark artifact under `metrics/runs/`.

At the end, report:
- screenshot path
- duration if measurable
- token usage if available
- tool call count if available
- visible tool count if available
- any fallback, timeout, pairing, scope-upgrade, or auth errors

Do not modify unrelated files.
```

### 3. GitHub PR Task

```text
Beta 3 performance benchmark: GitHub PR task.

In the public report repo, create a new branch, add one small benchmark note under `metrics/runs/`, commit it, push it, and open a PR.

At the end, report:
- branch
- commit
- PR URL
- duration if measurable
- token usage if available
- tool call count if available
- visible tool count if available
- any fallback, timeout, pairing, scope-upgrade, or auth errors

Do not modify unrelated files.
```

### 4. Full Workflow Task

```text
Beta 3 performance benchmark: full workflow task.

Run a complete Discord Codex harness workflow against:
https://github.com/jeffjhunter/openclaw-codex-harness-test-report

Requirements:
- create branch
- add one benchmark note under `metrics/runs/`
- commit and push
- open PR
- check PR checks/status
- check GitHub deployments/Vercel availability
- use actual browser tool to open the PR or repo and take screenshot
- post concise Discord summary

At the end, report:
- branch
- commit
- PR URL
- CI/check status
- deployment/Vercel status
- browser screenshot path
- duration if measurable
- token usage if available
- tool call count if available
- visible tool count if available
- any fallback, timeout, pairing, scope-upgrade, or auth errors

Do not use private repo links.
Do not modify unrelated files.
```

## Reporting Rule

Do not claim beta 3 is faster or more token efficient until repeated benchmark runs show that pattern.

Use cautious language:

- "Measured beta 3 run was lower/higher than beta 2 historical baseline."
- "Comparison is approximate because beta 2 data was historical, not controlled."
- "Code-mode architecture is confirmed; performance effect remains under measurement."
