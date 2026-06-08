# Phase E Changed Files Manifest

## Source repo

Repo: `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v6`

## Phase E modified files

| Path | Action | Purpose | Phase E status |
|---|---|---|---|
| `src/policy.js` | Modified | Add dashboard truth contract builder and status ranking | Included |
| `src/bootstrap.js` | Modified | Attach latest Docker evidence and dashboard truth contract to app state | Included |
| `src/server.js` | Modified | Expose dashboard truth status in `/api/health` | Included |
| `src/dashboard.js` | Modified | Render Dashboard Truth Contract table and mark token estimate | Included |
| `test/pala-v6.test.js` | Modified | Add Phase E fake-green and API contract tests | Included |
| `docs/dashboard-truth-contract.md` | Added | Document panel truth table and rules | Included |

## Required-but-not-mutated areas

| Path | Reason |
|---|---|
| `src/source-court.js` | Existing sanitized summary contract was reused; no Phase E mutation needed. |
| `.pala/state/last-dashboard-state.json` | Runtime/generated state; not committed as source artefact. |
| `src/config.js` | `DOCKER_EVIDENCE_DIR` already existed from earlier work. |

## Existing dirty files not introduced by Phase E

The source repo already had accumulated Phase A/B/C local mutations. They remain uncommitted and were not reverted.

```text
.github/CODEOWNERS
.github/PULL_REQUEST_TEMPLATE.md
.github/workflows/pala.yml
README.md
docs/github-policy-pack.md
docs/inheritance-backlog.json
docs/source-stamp-contract.md
docs/v6-dunya-standardi-karargah-tr.md
docs/v6-vibe-coder-agent-host-plan.md
scripts/pala_github_gate_audit.ps1
src/cli.js
src/config.js
src/core-foundation.js
src/environment-limits.js
src/operator-actions.js
src/source-court.js
.dockerignore
```

## Source repo final `git status --short`

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
?? docs/dashboard-truth-contract.md
?? docs/source-stamp-contract.md
?? docs/v6-vibe-coder-agent-host-plan.md
?? src/core-foundation.js
?? src/environment-limits.js
?? src/operator-actions.js
?? src/source-court.js
```

## Review package status

| Artefact | Status |
|---|---|
| Implementation Report | Present |
| Changed Files Manifest | Present |
| Repo Change Review | Present |
| Raw Patch/Diff | Present |

No Review Package = No Court Decision.
