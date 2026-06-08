# Phase D Changed Files Manifest

Source repo: `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v6`

Date: 2026-06-08

Phase: D - Docker + MCP Proof

Release posture: `RELEASE_BLOCKED`

## Phase D Source Repo Changes

No source repo file was intentionally changed in Phase D.

Phase D was a proof and evidence run.

## New Source Repo Files

None.

## Runtime Effects

Commands in Phase D may have touched local runtime evidence under ignored `.pala/**`.

The `.pala/**` runtime area is excluded from Docker context by `.dockerignore` and is not a source mutation package.

## Existing Dirty Worktree

The following dirty files existed from prior Phase A/B/C local mutation work and remain visible in `git status --short`:

```text
 M .github/CODEOWNERS
 M .github/PULL_REQUEST_TEMPLATE.md
 M .github/workflows/pala.yml
 M README.md
 M docs/github-policy-pack.md
 M docs/inheritance-backlog.json
 M docs/v6-dunya-standardi-karargah-tr.md
 M scripts/pala_github_gate_audit.ps1
 M src/bootstrap.js
 M src/cli.js
 M src/config.js
 M src/dashboard.js
 M src/policy.js
 M src/server.js
 M test/pala-v6.test.js
?? .dockerignore
?? docs/source-stamp-contract.md
?? docs/v6-vibe-coder-agent-host-plan.md
?? src/core-foundation.js
?? src/environment-limits.js
?? src/operator-actions.js
?? src/source-court.js
```

These are not Phase D changes.

## Phase D Commands

Docker commands:

```powershell
docker version
docker compose config
docker compose build
docker compose up -d
docker compose ps
docker compose logs --no-color
docker compose down
```

Local proof commands:

```powershell
curl.exe -sS http://127.0.0.1:8787/api/health
curl.exe -sS http://127.0.0.1:8787/api/state
node src/cli.js mcp health
node src/cli.js court
node src/cli.js source audit --json
npm.cmd test
git status --short
```

## Status

Changed-files manifest status: `PASS`

Phase D status: `PARTIAL`

Kanıtlanan durum budur.
RELEASE_BLOCKED.
