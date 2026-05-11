# OpenClaw Codex Benchmark Dashboard

This is a self-contained benchmark dashboard that visualizes run counts, pass/fail status, and average durations from the existing metrics data in the `metrics/` directory.

## How to View

1. Open `dashboard/index.html` in any modern web browser
2. The dashboard loads data from `dashboard/data.json` automatically
3. All metrics are derived from existing OpenClaw Codex harness benchmark runs

## Data Source

Metrics are sourced from:
- `metrics/summaries/2026-05-11-beta3-benchmark-rollup.md`
- `metrics/summaries/2026-05-11-beta3-browser-summary.md`
- `metrics/summaries/2026-05-11-beta3-github-pr-summary.md`
- `metrics/summaries/2026-05-11-beta3-minimal-file-summary.md`
- `metrics/summaries/2026-05-11-beta3-full-workflow-summary.md`

## Files Created

- `dashboard/index.html` - Main dashboard page with charts and tables
- `dashboard/data.json` - JSON data source for the dashboard (derived from existing metrics)
- `dashboard/README.md` - This documentation file

## Notes

- All metrics are derived from existing files only; no invented data.
- Unavailable metrics are marked as "N/A" or described in limitations.
- This is a static dashboard — no live updates or server-side components required.