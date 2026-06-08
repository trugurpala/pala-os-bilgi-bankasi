# Phase C Changed Files Manifest

Date: 2026-06-08
Source repo: `trugurpala/pala-os-v6`
Report: `2026-06-08-phase-c-implementation-report.md`

## Included In Phase C Package

New files:

- `.dockerignore`

Modified files:

- `.github/workflows/pala.yml`
- `src/bootstrap.js`
- `src/cli.js`
- `src/source-court.js`
- `test/pala-v6.test.js`

## Not Part Of Phase C Package / Pre-existing Dirty Surface

These paths were dirty before or outside the Phase C mutation intent. They should not be reviewed as Phase C work unless separately requested:

- `README.md`
- `docs/inheritance-backlog.json`
- `docs/v6-dunya-standardi-karargah-tr.md`
- `docs/source-stamp-contract.md`
- `docs/v6-vibe-coder-agent-host-plan.md`
- `src/config.js`
- `src/dashboard.js`
- `src/policy.js`
- `src/server.js`
- `src/core-foundation.js`
- `src/environment-limits.js`
- `src/operator-actions.js`

## Reviewer Should Check First

1. `.dockerignore`
2. `src/source-court.js`
3. `src/bootstrap.js`
4. `src/cli.js`
5. `test/pala-v6.test.js`
6. `.github/workflows/pala.yml`

## Evidence Commands

```powershell
rg "legacy/" src scripts test .github package.json Dockerfile compose.yaml
rg "legacy-skills-index" src skills test package.json
rg "legacy" src/dashboard.js src/server.js src/bootstrap.js
git ls-files legacy docs/legacy skills/registry/legacy-skills-index.json
node src/cli.js source audit --json
npm.cmd test
git status --short
docker build --no-cache -t pala-os-v6:phase-c .
```

## Evidence Summary

- `npm.cmd test`: `PASS`, 32/32.
- `node src/cli.js source audit --json`: `PARTIAL`, 0 blocked files, explicit legacy boundary `PASS`.
- `node src/cli.js court`: `RELEASE_BLOCKED`.
- Docker build: `NOT_AVAILABLE_WITH_REASON`, Docker daemon unavailable.

Kanıtlanan durum budur.
RELEASE_BLOCKED.
