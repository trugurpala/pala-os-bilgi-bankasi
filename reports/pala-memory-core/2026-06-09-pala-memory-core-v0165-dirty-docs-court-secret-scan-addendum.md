# Pala Memory Core v0.16.5 Dirty Docs Court Secret Scan Addendum

Date: 2026-06-09
Related report: `2026-06-09-pala-memory-core-v0165-dirty-docs-court-report.md`

## Correction / Clarification

The requested `Select-String -SimpleMatch` command returned no output because it treated the pipe-separated pattern as one literal string.

A stricter full-file scan found pre-existing documentation examples and policy words:

- Generic `C:\Users\you` examples in `README.md` and `INSTALL.md`
- Existing `secret` policy references in `README.md`, `docs/backlog.md`, `docs/roadmap.md`, and `docs/v0.1-acceptance.md`

These were not introduced by the v0.16.5 dirty docs diff.

## Diff-Added-Line Scan

The committed added lines for v0.16.5 were scanned for:

```text
C:\Users
Pala-Home-1
OPENAI_API_KEY
sk-
ghp_
token
secret
password
.env
```

Result: no matches in newly added lines.

## Decision Impact

The `KEEP_IN_DOCS_PR` decision remains valid because the v0.16.5 changes add only sync closeout documentation and do not introduce secrets or owner-local paths.
