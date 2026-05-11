# OpenClaw Beta 2 Codex Harness Public Report

Date: 2026-05-11

OpenClaw version tested: `2026.5.10-beta.2`

## Summary

OpenClaw beta 2 successfully completed real Codex harness workflows through Discord, including shell/filesystem work, GitHub branch and PR creation, browser automation, CI status inspection, Vercel deployment inspection, and Discord reporting.

The harness was useful end-to-end, but testing found upgrade and observability issues around plugin state, Discord live reactions, browser CLI authentication context, Vercel preview access, and runtime model identity.

## Confirmed Passes

| Area | Result |
| --- | --- |
| Codex coding workflow | PASS |
| Browser automation through the actual OpenClaw browser tool | PASS |
| Shell/filesystem work | PASS |
| GitHub branch, commit, push, and PR creation | PASS |
| CI status inspection | PASS |
| Vercel deployment inspection | PASS |
| Discord message reporting | PASS |

## Findings

### Codex plugin required explicit install after update

After upgrading to beta 2, the Codex plugin was not available until it was explicitly installed again.

Expected behavior: updating to beta should preserve or automatically load the Codex plugin when Codex harness is in use.

Impact: users upgrading into Codex harness testing may see missing harness functionality until the plugin is manually reinstalled or re-enabled.

### Discord plugin appeared offline after update

After upgrading, OpenClaw appeared offline in Discord until plugin/config state was corrected and services were restarted.

Expected behavior: Discord integration should remain enabled and online across beta updates.

### Discord live reactions were missing after update

After upgrading, OpenClaw only added an acknowledgement reaction and did not provide live status reactions during message handling.

Local status: fixed after status reactions were explicitly enabled. Live reactions were confirmed working again.

### Browser tool worked, but shell CLI browser path had an auth/context mismatch

The actual OpenClaw browser tool succeeded with status/start/open/snapshot/interaction/screenshot operations.

Separately, invoking the browser shell CLI from the Codex app-server context failed with a gateway-token/auth-context issue.

Important distinction: this was not a browser automation failure. The Codex-accessible browser tool worked.

### Vercel PR preview was Ready but HTTP verification returned 401

The Vercel preview deployment was reported Ready, but direct HTTP verification returned `401` instead of `200`.

The harness correctly treated this as a preview HTTP verification failure.

This may be expected if preview protection is enabled, but the result should be reported explicitly.

### Runtime model identity could not be independently proven

The test environment was configured for OpenAI `gpt-5.5`, and no fallback evidence was observed.

However, the harness did not expose a runtime `/status` equivalent or model-introspection command that independently proved the active provider/model/fallback state from inside the thread.

## Capability Matrix

| Capability | Result |
| --- | --- |
| Codex runtime identity | FAIL |
| Browser tool | PASS |
| Shell/filesystem | PASS |
| GitHub branch/commit/PR | PASS |
| CI status check | PASS |
| Vercel preview HTTP 200 verification | FAIL |
| Discord message send | PASS |

## Beta 3 Follow-Up

OpenClaw developers reported that beta 3 starts Codex harness threads with:

```text
features.code_mode = true
features.code_mode_only = true
```

Developer-provided expected effects:

- Dynamic tools run inside Codex's native code/search/tool surface.
- Fewer duplicate tool-search abstractions.
- Better alignment with real Codex coding sessions.
- Improved speed and lower token use.

Beta 3 should be tested with the same scenarios used for beta 2 to compare behavior directly.
