# Pala Memory Core v0.19 Changed Files Manifest

## Included Files

| File | Status | Reason |
|---|---|---|
| `.github/workflows/pala-memory-core-ci.yml` | Modified | Adds CI existence checks for Codex compatibility docs and templates. |
| `AGENTS.md` | Modified | Adds Codex operating protocol while preserving existing project and knowledge-bank guidance. |
| `docs/codex-compatibility.md` | New | Documents the evidence-first Codex workflow. |
| `docs/commands.md` | Modified | Adds the `codex compatibility` documentation section. |
| `docs/task-templates/codex-audit-task.md` | New | Adds audit task template. |
| `docs/task-templates/codex-feature-task.md` | New | Adds feature task template. |
| `docs/task-templates/codex-merge-gate.md` | New | Adds merge gate task template. |
| `pala.py` | Modified | Adds doctor checks for Codex protocol files, required smoke, forbidden files, and product truth. |

## Excluded Files

| Pattern | Reason |
|---|---|
| `dashboard/records.json` | Generated dashboard export. |
| `data/reports/*` | Generated intelligence reports. |
| `data/backups/*` | Backup package history. |
| `data/records/*` | Runtime memory records. |
| `.env` | Secret-bearing local config. |
| `.pala/config.json` | Local user config. |

## New Files

- `docs/codex-compatibility.md`
- `docs/task-templates/codex-audit-task.md`
- `docs/task-templates/codex-feature-task.md`
- `docs/task-templates/codex-merge-gate.md`

## Pre-existing Dirty Files

None observed before commit.
