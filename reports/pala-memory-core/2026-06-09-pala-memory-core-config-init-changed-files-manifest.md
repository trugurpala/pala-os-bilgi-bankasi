# Pala Memory Core Config Init Changed Files Manifest

Date: 2026-06-09
Source repo: `trugurpala/pala-memory-core`
Source commit: `0c9334bc1dd3d987440c393c71a5b8365f2164d4`
Phase: local config/init preview
Status: PASS

## Included Product Files

| File | Status | Notes |
|---|---|---|
| `.gitignore` | Modified | Ignores user-specific `pala.config.json`. |
| `pala.py` | Modified | Adds config helpers, `init`, config-aware path defaults, doctor config checks, and dashboard host/port defaults. |
| `pala.config.example.json` | New | Adds committed example config. |
| `README.md` | Modified | Adds init/config to quickstart, layers, layout, and command table. |
| `INSTALL.md` | Modified | Adds init/config to install and daily-use guidance. |
| `docs/backlog.md` | Modified | Adds init/config backlog items. |
| `docs/commands.md` | Modified | Documents `init` options. |
| `docs/roadmap.md` | Modified | Adds v0.15 config/init milestone. |
| `docs/v0.1-acceptance.md` | Modified | Adds config init acceptance rows. |
| `docs/v0.15-config-init.md` | New | Adds phase report and smoke evidence. |

## Excluded Dirty Files

| Path | Reason |
|---|---|
| `pala.config.json` | User-specific local config, intentionally ignored by Git. |

## Generated But Not Included

| Path | Reason |
|---|---|
| `data/backups/` config smoke packages | Generated smoke backup packages are ignored by `.gitignore`. |
| `data/inbox/` config smoke folders | Generated local runtime data is ignored by `.gitignore`. |
| `dashboard/records.json` | Generated dashboard data is ignored by `.gitignore`. |
| `data/records/` | Local runtime records are ignored by `.gitignore`. |

## New Files

- `pala.config.example.json`
- `docs/v0.15-config-init.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-config-init-implementation-report.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-config-init-changed-files-manifest.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-config-init-repo-change-review.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-config-init-raw-patch-diff.patch`

## Backup Package

Redacted all-scope backup package:

`reports/pala-memory-core-backups/2026-06-09-20260609T143707Z-pala-memory-core-all-backup`

Knowledge-bank backup commit:

`86800aecd0ec7cdc30a5a68756331b6ef4310b9f`
