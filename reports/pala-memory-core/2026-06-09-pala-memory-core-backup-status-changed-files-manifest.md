# Pala Memory Core Backup Status Changed Files Manifest

Date: 2026-06-09
Source repo: `trugurpala/pala-memory-core`
Source commit: `2935ef1cce07275dc825a8d89e1dfbfe2a3cc823`
Phase: backup status tracking preview
Status: PASS

## Included Product Files

| File | Status | Notes |
|---|---|---|
| `pala.py` | Modified | Added record persistence helpers and backup status updates after receipt/GitHub/Drive backup commands. |
| `README.md` | Modified | Added v0.14 backup status tracking command table row. |
| `INSTALL.md` | Modified | Added all-record backup/status daily-use command. |
| `docs/backlog.md` | Modified | Added backup status tracking backlog item. |
| `docs/commands.md` | Modified | Documented status updates for receipt, GitHub, and Drive backup commands. |
| `docs/roadmap.md` | Modified | Added v0.14 backup status tracking milestone. |
| `docs/v0.1-acceptance.md` | Modified | Added backup status tracking acceptance rows. |
| `docs/v0.14-backup-status-tracking.md` | New | Added phase report and smoke evidence. |

## Excluded Dirty Files

None.

## Generated But Not Included

| Path | Reason |
|---|---|
| `data/records/` | Local runtime record status updates are ignored by `.gitignore`. |
| `data/reports/2026-06-09-vault-all-report.md` | Generated runtime report is ignored by `.gitignore`. |
| `data/backups/` smoke packages | Generated smoke backup packages are ignored by `.gitignore`. |
| `dashboard/records.json` | Generated dashboard data is ignored by `.gitignore`. |

## New Files

- `docs/v0.14-backup-status-tracking.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-backup-status-implementation-report.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-backup-status-changed-files-manifest.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-backup-status-repo-change-review.md`
- `reports/pala-memory-core/2026-06-09-pala-memory-core-backup-status-raw-patch-diff.patch`

## Backup Package

Redacted all-scope backup package:

`reports/pala-memory-core-backups/2026-06-09-20260609T142751Z-pala-memory-core-all-backup`

Knowledge-bank backup commit:

`d5bb251e0932b549eb11013889f1696bcce5ae20`
