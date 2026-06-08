# Phase A Changed Files Manifest

Date: 2026-06-08
Source repo: `trugurpala/pala-os-v6`
Report: `2026-06-08-phase-a-source-court-hardening.md`

## Included In Phase A Package

New files:

- `src/source-court.js`
- `docs/source-stamp-contract.md`

Modified files:

- `src/config.js`
- `src/policy.js`
- `src/bootstrap.js`
- `src/cli.js`
- `test/pala-v6.test.js`
- `docs/inheritance-backlog.json`
- `docs/v6-dunya-standardi-karargah-tr.md`

## Excluded From Phase A Package

These paths were already dirty or outside the approved Phase A mutation scope. They were not part of the Phase A package:

- `README.md`
- `src/dashboard.js`
- `src/server.js`
- `docs/v6-vibe-coder-agent-host-plan.md`
- `src/core-foundation.js`
- `src/environment-limits.js`
- `src/operator-actions.js`

## Evidence Commands

```powershell
rg "@palaSourceRef|@palaCourtDecision" src scripts docs plans prompts AGENTS.md README.md
node src/cli.js source audit --json
node src/cli.js court
npm.cmd test
git status --short
```

## Status

- Source Court validator: implemented
- Tests: `PASS`
- Source stamp gate: `PARTIAL`
- Release: `RELEASE_BLOCKED`

Kanıtlanan durum budur.
RELEASE_BLOCKED.
