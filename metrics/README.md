# Codex Harness Performance Metrics

This folder tracks performance and token-efficiency measurements for OpenClaw Codex harness testing.

## Goal

Validate the beta 3 code-mode claim carefully:

> Codex harness threads now run with `features.code_mode = true` and `features.code_mode_only = true`, moving dynamic/searchable tools into Codex's native code/search/tool surface. Practical effect should be faster operation and fewer tokens.

Developer feedback received after initial testing:

- Code mode is experimental.
- Current interest is Codex specifically, because code mode is default there.
- CLI scope-upgrade behavior is separate and needs further research.

## Measurement Rules

Performance claims require comparable runs. A run is comparable only when these are held stable:

- OpenClaw channel path, such as Discord harness vs CLI vs TUI
- Codex harness path only for the code-mode benchmark
- Model and provider
- Prompt text
- Repository and task scope
- Fresh vs continued session state
- Required external services, such as GitHub, browser, CI, or Vercel

## Metrics To Record

| Metric | Purpose |
| --- | --- |
| Wall-clock duration | User-visible speed |
| Input tokens | Prompt/tool context size |
| Output tokens | Response generation size |
| Cache read/write tokens | Context reuse behavior |
| Total tokens | Overall model token cost |
| Tool call count | Tooling overhead |
| Visible tool count | Tool-surface size |
| Fallback/errors | Whether the run is valid for comparison |

## Benchmark Task Set

| Task | Purpose |
| --- | --- |
| Minimal file task | Measures baseline harness overhead. |
| Browser task | Measures browser/tool path overhead. |
| GitHub PR task | Measures real coding workflow overhead. |
| Full workflow task | Measures end-to-end Discord + browser + GitHub workflow. |

## Current Data Quality

Beta 2 has useful historical telemetry from trajectory/session files, but it was not collected as a controlled benchmark suite. It can be used as a rough baseline only.

Beta 3 should be measured with repeated same-prompt runs before making a strong speed/token-efficiency claim.

Recommended threshold for a careful conclusion:

- At least 3 beta 3 runs per benchmark task.
- Compare against beta 2 only when prompt/task shape is close enough.
- Label non-identical comparisons as approximate.
