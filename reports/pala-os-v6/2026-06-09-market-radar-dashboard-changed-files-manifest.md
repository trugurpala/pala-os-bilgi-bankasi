# Pala OS V6 Market Radar Dashboard - Changed Files Manifest

Date: 2026-06-09  
Source repo: `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v6`  
Phase: Market radar dashboard implementation  
Status: `PASS` for local implementation package

## Included Source Files

| Path | Status | Purpose |
| --- | --- | --- |
| `.pala/rules/market-radar.json` | New | Machine-readable core 10 market radar catalog. |
| `src/market-radar.js` | New | Loads, seeds, summarizes, and source-card-annotates market radar references. |
| `src/config.js` | Modified | Adds `MARKET_RADAR_PATH`. |
| `src/bootstrap.js` | Modified | Seeds market radar catalog and includes radar state in app state. |
| `src/server.js` | Modified | Adds `GET /api/market-radar`. |
| `src/dashboard.js` | Modified | Replaces hard-coded reference doctrine with state-backed World Agent Control Radar panel. |
| `src/cli.js` | Modified | Extends `sak ingest` with `--decision`, `--risk`, `--layer`, and `--evidence-uri`. |
| `test/pala-v6.test.js` | Modified | Adds tests for core 10 catalog, market radar API/dashboard HTML, and ingest flag persistence. |
| `docs/oss-upstream-matrix.md` | Modified | Documents core 10 radar and `phuryn/pm-skills` PM/shipping doctrine boundary. |

## New Source Files

| Path | Purpose |
| --- | --- |
| `.pala/rules/market-radar.json` | Source-backed market radar catalog visible to dashboard/API. |
| `src/market-radar.js` | Runtime loader and summarizer for market radar state. |

## Excluded Dirty Files

| Path | Reason |
| --- | --- |
| `.pala/rules/world-standards.json` | Pre-existing line-ending dirty state; no content diff included. |
| `docs/v6-vibe-coder-agent-host-plan.md` | Pre-existing untracked plan document; not part of this implementation. |
| `legacy/` | Pre-existing untracked legacy/runtime files; not part of this implementation. |
| `.pala/evidence/screenshots/market-radar-dashboard.png` | Local visual evidence only; ignored runtime output. |
| `.pala/evidence/screenshots/market-radar-dashboard-tall.png` | Local visual evidence only; ignored runtime output. |

## Knowledge-Bank Files Added

| Path | Purpose |
| --- | --- |
| `reports/pala-os-v6/2026-06-09-market-radar-dashboard-implementation-report.md` | Implementation report. |
| `reports/pala-os-v6/2026-06-09-market-radar-dashboard-changed-files-manifest.md` | This manifest. |
| `reports/pala-os-v6/2026-06-09-market-radar-dashboard-repo-change-review.md` | Repo change review package. |
| `reports/pala-os-v6/2026-06-09-market-radar-dashboard-raw-patch-diff.patch` | Raw patch/diff for the source mutation package. |

## Source Commit Scope

Source commit:

- Not created.

Push status:

- Source repo was not pushed.
- Knowledge-bank publication is separate and does not approve source release.

## Evidence Summary

- Full test suite passed: 13/13.
- `.\sak.cmd status` shows 0 blocked required standards.
- `.\sak.cmd audit` reports `PARTIAL`.
- `.\sak.cmd court` reports `RELEASE_BLOCKED`.
- `/api/market-radar` returns HTTP 200 with 10 references.
- Headless Chrome screenshot confirms the dashboard renders the new market radar panel.

## Release Posture

This manifest is not release approval. Release remains owner-controlled and blocked in normal state.
