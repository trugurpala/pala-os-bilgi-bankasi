# Pala Memory Core Recovery Search Changed Files Manifest

Date: 2026-06-09
Source repo: `trugurpala/pala-memory-core`
Source commit: `0dba166f6ea9b34be0c03357045a8419d5f876a2`
Phase: recovery search preview
Status: PASS, with browser snapshot blocked by missing Chrome Playwright Extension

## Included Product Files

| File | Status | Notes |
|---|---|---|
| `pala.py` | Modified | Added all-record loading, filters, `list`, `search`, `show`, and dashboard `--all` export. |
| `dashboard/index.html` | Modified | Added search input and client-side filtering for exported records. |
| `schema/record.schema.json` | Modified | Added `mobile` and `playwright` source enum values. |
| `README.md` | Modified | Added recovery commands and dashboard `--all` usage. |
| `INSTALL.md` | Modified | Added daily-use recovery commands. |
| `docs/backlog.md` | Modified | Added search/dashboard filtering backlog items. |
| `docs/commands.md` | Modified | Documented `list`, `search`, `show`, and dashboard `--all`. |
| `docs/roadmap.md` | Modified | Aligned release history and added recovery search milestone. |
| `docs/v0.1-acceptance.md` | Modified | Added recovery acceptance checks. |
| `docs/v0.11-recovery-search.md` | New | Added phase report and smoke evidence. |

## Excluded Dirty Files

None.

## Generated But Not Included

| Path | Reason |
|---|---|
| `dashboard/records.json` | Generated dashboard data is ignored by `.gitignore`. |
| `data/records/` | Local runtime records are ignored by `.gitignore`. |
| `data/reports/` | Local runtime reports are ignored by `.gitignore`. |
| `data/attachments/` | Local attachments are ignored by `.gitignore`. |
| `data/backups/` | Local backup staging is ignored by `.gitignore`. |

## New Files

- `docs/v0.11-recovery-search.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-recovery-search-implementation-report.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-recovery-search-changed-files-manifest.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-recovery-search-repo-change-review.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-recovery-search-raw-patch-diff.patch`

## Backup Package

Redacted backup package:

`reports/pala-memory-core-backups/2026-06-09-20260609T140411Z-pala-memory-core-backup`

Knowledge-bank backup commit:

`e879dbf013c1d0742a2b2d950103bed0ca9322a5`
