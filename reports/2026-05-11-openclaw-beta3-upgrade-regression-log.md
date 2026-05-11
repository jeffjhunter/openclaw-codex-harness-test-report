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
| 2026-05-11T05:26Z | Verified installed Codex source | Installed Codex beta 3 source contains `features.code_mode = true` and `features.code_mode_only = true` in thread lifecycle setup. |
| 2026-05-11T05:27Z | Checked Discord channel status | Discord channel was configured, running, and connected after upgrade. |
| 2026-05-11T05:27Z | Checked browser/live reaction config | Browser plugin enablement and status reactions remained enabled after upgrade. |
| 2026-05-11T05:28Z | Ran direct CLI agent smoke test | Gateway route failed due pending scope upgrade; command fell back to embedded execution. |
| 2026-05-11T05:31Z | Reviewed smoke test metadata | Embedded run still reported Codex harness metadata, OpenAI provider, `gpt-5.5`, and dynamic tools visible through Codex tool registry. |
| 2026-05-11T05:32Z | Tested device scope approval | CLI device approval flow repeatedly generated new scope-upgrade requests and failed to approve the original request. |
| 2026-05-11T05:41Z | Ran live Discord harness regression audit | Clean Discord harness path completed with actual browser tool, GitHub public repo access, Discord send, and no fallback/scope/pairing/auth errors observed. |

## Initial Upgrade Observations

- Update completed successfully.
- Codex and Discord plugins were updated from beta 2 to beta 3.
- During the update flow, doctor output briefly reported the gateway as not running.
- A subsequent gateway status check showed the gateway service active and running on beta 3.
- The updater rewrote the OpenClaw config and created a backup.
- Installed beta 3 Codex source confirms the developer-provided code-mode flags are present.
- Discord remained connected after the beta 3 update.
- Browser enablement and status reaction config remained enabled after the beta 3 update.
- The browser shell CLI still hit a gateway scope-upgrade/pairing failure.
- The direct `openclaw agent` CLI path also hit a gateway scope-upgrade/pairing failure and fell back to embedded execution.
- The embedded fallback smoke test reported Codex harness metadata, but this should not be treated as equivalent to a clean gateway-routed Discord harness test.
- The CLI device approval command could identify the pending scope-upgrade request, but explicit approval generated a new pending request and then failed with `unknown requestId`.
- The live Discord harness path did not reproduce the CLI scope-upgrade issue. It completed normally.
- Runtime metadata still did not expose explicit `features.code_mode` or `features.code_mode_only` fields, even though installed beta 3 source contains those flags.
- Dynamic tools were visible directly in the Codex tool surface, including OpenClaw tools and Codex Apps MCP tools.

## Beta 3 Smoke Test Results

| Check | Result | Notes |
| --- | --- | --- |
| Installed OpenClaw version | PASS | CLI and gateway reported `2026.5.10-beta.3`. |
| Codex plugin version | PASS | Codex plugin reported `2026.5.10-beta.3`. |
| Discord plugin version | PASS | Discord plugin reported `2026.5.10-beta.3`. |
| Gateway running after update | PASS | Gateway was active after update handoff. |
| Discord connected after update | PASS | Discord account was running and connected. |
| Browser config survived update | PASS | Browser enablement remained true. |
| Status reactions survived update | PASS | Status reactions remained enabled. |
| Code-mode flags present in installed source | PASS | `features.code_mode` and `features.code_mode_only` were present in Codex beta 3 thread lifecycle code. |
| Code-mode visible in live runtime metadata | PARTIAL | Source confirms flags, but explicit runtime metadata field was not exposed in the smoke-test result. |
| Dynamic tools visible through Codex-native surface | PASS | Smoke test observed OpenClaw dynamic tools and Codex app connector tools in the Codex tool registry. |
| Dedicated `tool_search` tool visible | FAIL | No dedicated `tool_search` tool was visible in the smoke test. This may be expected under code-mode-only behavior. |
| Gateway-routed CLI agent run | FAIL | CLI requested broader scopes and gateway rejected it pending approval. |
| CLI device scope approval | FAIL | Approval flow generated another scope-upgrade request and then failed with `unknown requestId`. |
| Browser shell CLI | FAIL | Browser CLI continued to fail on gateway scope-upgrade/pairing. |

## Live Discord Harness Regression Audit

The live Discord harness regression test completed successfully after the beta 3 upgrade.

| Check | Result | Notes |
| --- | --- | --- |
| OpenClaw beta 3 confirmed | PASS | Harness reported `2026.5.10-beta.3`. |
| Codex plugin beta 3 confirmed | PASS | Harness found Codex plugin install metadata for `2026.5.10-beta.3`. |
| Codex harness path | PASS WITH LIMITATION | Codex/OpenClaw harness context and tools were present; no separate `/status` proof was exposed. |
| `features.code_mode=true` runtime visibility | NOT VISIBLE | The exact feature flag was not exposed in runtime metadata available to the harness. |
| `features.code_mode_only=true` runtime visibility | NOT VISIBLE | The exact feature flag was not exposed in runtime metadata available to the harness. |
| Dynamic tools discoverable | PASS | Harness observed 208 visible tools through tool introspection. |
| Tool layer assessment | PASS | Tools appeared as Codex-native declarations, including directly surfaced OpenClaw and Codex Apps MCP tools. No explicit `tool_search` tool was visible. |
| Browser tool | PASS | Actual OpenClaw browser tool opened the public report repository, captured a snapshot, and saved a screenshot. |
| GitHub public repo access | PASS | GitHub CLI returned public repository metadata. |
| Discord message send | PASS | OpenClaw message tool posted progress and completion messages. |
| Fallback/timeout/scope/pairing/auth errors | PASS | None were observed in the live Discord harness path. |

## Regression Tests To Run

| Test | Status |
| --- | --- |
| Verify Codex harness thread exposes or implies code mode | Partial |
| Verify dynamic tools are discoverable through Codex-native surface | Pass |
| Repeat browser automation with actual OpenClaw browser tool | Pass |
| Repeat GitHub branch/commit/PR workflow | Partial |
| Repeat CI status inspection | Pending |
| Repeat Vercel preview detection and HTTP verification | Pending |
| Repeat Discord live reaction behavior | Pass |
| Check runtime model/provider/fallback observability | Partial |

## Open Questions

1. Is code mode visible from any local status, session metadata, or transcript field?
2. Does beta 3 remove duplicate tool-search behavior inside Codex harness sessions?
3. Does beta 3 preserve Discord live reaction behavior after upgrade?
4. Does beta 3 change browser shell CLI authentication behavior from the Codex app-server context?
5. Why does the CLI device approval flow create a new scope-upgrade request while attempting to approve the previous one?
6. Should beta 3 expose code-mode/code-mode-only state through a status or runtime metadata field for easier verification?
