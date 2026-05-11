# Benchmark Dashboard

This directory contains a static dashboard for the committed OpenClaw Codex harness benchmark metrics.

## Files

- dashboard/index.html - plain HTML/CSS/JS dashboard.
- dashboard/data.json - structured benchmark data derived from committed markdown files under metrics/.
- dashboard/README.md - viewing notes and evidence summary.

## View Locally

From the repository root:

    python3 -m http.server 4173

Then open:

    http://127.0.0.1:4173/dashboard/

The page fetches dashboard/data.json, so it should be viewed through a local static server rather than directly from a file URL.

## Evidence Summary

The dashboard data was derived from the existing committed metrics files only. No benchmark values were invented. Metrics that are not exposed by the source artifacts are marked unavailable or null in data.json.

Verified source coverage:

- 4 benchmark task groups.
- 12 benchmark run files.
- 5 benchmark summary files.
- Average durations from source run durations:
  - Minimal file: 0.036s
  - Browser: 2.221s
  - GitHub PR: 6.575s
  - Full workflow: 8.477s

Known limitations preserved in the dashboard:

- Per-run token usage is unavailable; source files expose session-level snapshots only.
- Exact isolated per-run total tool-call counts are unavailable.
- Beta 2 data is historical rather than a controlled same-prompt benchmark.
- This repository reported no CI checks or GitHub deployments in benchmark runs, so CI and Vercel timing were unavailable.
- Prior screenshot captures are described in source files, but exact prior screenshot paths are unavailable in committed metric files.
