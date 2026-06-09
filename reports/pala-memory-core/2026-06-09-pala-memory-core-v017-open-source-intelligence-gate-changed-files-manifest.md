# Pala Memory Core v0.17 Changed Files Manifest

## Included Mutation Package
| File | Status | Change Notes |
|---|---|---|
| `.github/workflows/pala-memory-core-ci.yml` | included | Adds offline source court smoke and generated hygiene coverage. |
| `dashboard/index.html` | included | Adds Open Source Intelligence Court cards and candidate table. |
| `docs/commands.md` | included | Documents `source court` command, outputs, and decisions. |
| `docs/open-source-candidates.json` | new | Adds candidate registry for MCP, SDK, Vibe, and security discovery leads. |
| `docs/open-source-intelligence.md` | new | Adds policy document for source visibility, license, token intake, and safety. |
| `pala.py` | included | Adds source court CLI, offline/online evaluation, generated report, doctor checks, and dashboard export payload. |

## Excluded Runtime Artifacts
| File | Reason |
|---|---|
| `data/reports/open-source-intelligence.json` | generated, gitignored |
| `data/reports/token-intelligence.json` | generated, gitignored |
| `dashboard/records.json` | generated, gitignored |
| `data/records/*` | runtime memory records, gitignored |
| `pala.config.json` | local config, gitignored |

## Stage Policy
Only the six source/docs/CI files above were staged in the source repo commit.
