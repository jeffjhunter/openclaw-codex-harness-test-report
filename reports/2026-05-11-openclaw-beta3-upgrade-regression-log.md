# OpenClaw Beta 3 Upgrade and Regression Log

Date: 2026-05-11

## Purpose

Track upgrade behavior and regression testing for OpenClaw beta 3 after beta 2 Codex harness testing.

## Developer-Provided Beta 3 Context

OpenClaw developers reported that beta 3 starts Codex harness threads with:

```text
features.code_mode = true
features.code_mode_only = true
```

Expected effect:

- Codex harness threads should use Codex-native code mode.
- Dynamic tools should be discoverable through Codex's native code/search/tool surface.
- OpenClaw's PI-style tool-search layer should be less prominent or no longer duplicated in Codex harness threads.

## Upgrade Log

| Time UTC | Action | Result |
| --- | --- | --- |
| 2026-05-11T05:20:26Z | Captured pre-upgrade baseline | System was on `2026.5.10-beta.2`; registry target showed beta 3 available. |
| 2026-05-11T05:21Z | Ran non-interactive beta update | Update completed from beta 2 to beta 3. |
| 2026-05-11T05:23Z | Update rewrote OpenClaw config | Config backup was created by updater. |
| 2026-05-11T05:24Z | Verified installed CLI version | CLI reported `2026.5.10-beta.3`. |
| 2026-05-11T05:24Z | Verified gateway service | Gateway service was running on beta 3 after update handoff. |

## Initial Upgrade Observations

- Update completed successfully.
- Codex and Discord plugins were updated from beta 2 to beta 3.
- During the update flow, doctor output briefly reported the gateway as not running.
- A subsequent gateway status check showed the gateway service active and running on beta 3.
- The updater rewrote the OpenClaw config and created a backup.

## Regression Tests To Run

| Test | Status |
| --- | --- |
| Verify Codex harness thread exposes or implies code mode | Pending |
| Verify dynamic tools are discoverable through Codex-native surface | Pending |
| Repeat browser automation with actual OpenClaw browser tool | Pending |
| Repeat GitHub branch/commit/PR workflow | Pending |
| Repeat CI status inspection | Pending |
| Repeat Vercel preview detection and HTTP verification | Pending |
| Repeat Discord live reaction behavior | Pending |
| Check runtime model/provider/fallback observability | Pending |

## Open Questions

1. Is code mode visible from any local status, session metadata, or transcript field?
2. Does beta 3 remove duplicate tool-search behavior inside Codex harness sessions?
3. Does beta 3 preserve Discord live reaction behavior after upgrade?
4. Does beta 3 change browser shell CLI authentication behavior from the Codex app-server context?
