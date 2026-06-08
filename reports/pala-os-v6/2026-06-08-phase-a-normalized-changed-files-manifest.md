# Phase A Normalized Changed Files Manifest

## Scope

This manifest normalizes the Phase A Source Court hardening package for review completeness. It is not a new source mutation.

## Phase A file set

| File | Role | Include in Phase A review? | Notes |
|---|---|---:|---|
| `src/source-court.js` | Source Court validator | Yes | New validator surface for active discovery, classification, stamps, cards, court decisions, verdicts. |
| `docs/source-stamp-contract.md` | Source stamp contract | Yes | Defines classification semantics, PASS/PARTIAL/BLOCKED rules, release evidence limits. |
| `src/config.js` | Paths/config | Yes | Adds/anchors Source Court contract and evidence paths. |
| `src/policy.js` | Court policy integration | Yes | Source stamp gate evaluation and later shared truth logic live here. |
| `src/bootstrap.js` | App state integration | Yes | Source Court audit and source stamp gate are attached to app state/court. |
| `src/cli.js` | CLI command surface | Yes | Exposes `source audit --json` and court integration. |
| `test/pala-v6.test.js` | Test coverage | Yes | Covers classification, PASS chain, CLI JSON, court gate, legacy boundary. |
| `docs/inheritance-backlog.json` | Source court decision evidence | Yes | Adds source court decision for adapted governance doc. |
| `docs/v6-dunya-standardi-karargah-tr.md` | Adapted governance doc | Yes | Contains source stamp tying adapted legacy governance content to Source Court. |

## Explicitly not Phase A

| File | Reason |
|---|---|
| `.dockerignore` | Phase C legacy/Docker boundary. |
| `.github/CODEOWNERS` | Phase B governance. |
| `.github/PULL_REQUEST_TEMPLATE.md` | Phase B governance. |
| `docs/github-policy-pack.md` | Phase B governance. |
| `docs/dashboard-truth-contract.md` | Phase E dashboard truth. |
| `src/server.js` | Phase C/E API boundary and dashboard truth. |
| `README.md` | Unknown/owner-scope court item. |
| `docs/v6-vibe-coder-agent-host-plan.md` | Separate product/agent-host plan candidate. |
| `src/core-foundation.js` | Unknown/owner-scope court item. |
| `src/environment-limits.js` | Unknown/owner-scope court item. |
| `src/operator-actions.js` | Unknown/owner-scope court item. |

## Review package status

| Artefact | Status |
|---|---|
| Normalized Implementation Report | Present |
| Normalized Changed Files Manifest | Present |
| Normalized Repo Change Review | Present |
| Normalized Raw Patch/Diff | Present |

Phase A review package: `PASS`.

Phase A runtime source gate: `PARTIAL`.
