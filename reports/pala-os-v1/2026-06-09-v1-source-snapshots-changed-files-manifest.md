# Changed Files Manifest - v1 Source Snapshot Ingest

Date: 2026-06-09
Source repo: `trugurpala/pala-os`
Branch: `codex/v1-source-snapshots`
Commit: `ce098b3`
PR: https://github.com/trugurpala/pala-os/pull/163
Status: `PARTIAL`

## Included Files

| Path | State | Count | Purpose |
| --- | --- | ---: | --- |
| `docs/source-ingest/2026-06-09-v1-source-snapshots.md` | New | 1 | Court/manifest for the v1 source ingest. |
| `source-snapshots/README.md` | New | 1 | Local rules and source table for snapshots. |
| `source-snapshots/raw/pala-os/**` | New | 1211 | Snapshot of v1/default source. |
| `source-snapshots/raw/pala-os-v3/**` | New | 294 | Snapshot of v3/default source. |
| `source-snapshots/raw/pala-os-v4/**` | New | 245 | Snapshot of v4/default source. |
| `source-snapshots/raw/pala-os-v5/**` | New | 59 | Snapshot of v5/default source. |

Total new files in commit: `1811`.

The full file-name list is included in `2026-06-09-v1-source-snapshots-raw-patch-diff.patch` as `git show --name-status` output. Full patch body is intentionally not published because the source repository is private and the content is large.

## Excluded Dirty Files

| Path | Reason |
| --- | --- |
| `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v4` | Local folder name says v4, but remote is `trugurpala/pala-os-v6.git`; worktree also had local dirty changes. |
| `C:\Users\Pala-Home-1\Documents\pala-os-v1` | Commitsiz, remote-less git shell; not the GitHub v1 source. |

## New Knowledge-Bank Files

| File | Purpose |
| --- | --- |
| `reports/pala-os-v1/2026-06-09-v1-source-snapshots-implementation-report.md` | Owner-readable implementation report. |
| `reports/pala-os-v1/2026-06-09-v1-source-snapshots-changed-files-manifest.md` | This manifest. |
| `reports/pala-os-v1/2026-06-09-v1-source-snapshots-repo-change-review.md` | Review package and risk notes. |
| `reports/pala-os-v1/2026-06-09-v1-source-snapshots-raw-patch-diff.patch` | Redacted raw diff/name-status artifact. |

## Release Posture

`BLOCKED`. Snapshot ingest does not approve release or runtime activation.
