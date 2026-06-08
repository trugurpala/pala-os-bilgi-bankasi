# Append-Only Report Policy

Owner directive date: 2026-06-08

Pala OS knowledge-bank reports must be append-only.

Rules:

- Do not overwrite an existing report file with a new report.
- Every new report must use a new filename.
- Use a dated filename with phase and purpose.
- If the same phase needs another report on the same day, add a sequence suffix.
- Keep old reports and manifests so review history remains visible.
- Corrections should be published as a new correction/addendum file, not by silently replacing the old report.

Filename examples:

- `2026-06-08-phase-c-implementation-report.md`
- `2026-06-08-phase-c-implementation-report-v2.md`
- `2026-06-08-phase-c-addendum-docker-proof.md`
- `2026-06-08-phase-b-final-mutation-scope.md`

Exception:

- Index files such as `README.md` may be updated to point to newer reports, but report bodies and manifests should remain append-only unless the owner explicitly requests an edit.

Owner phrase:

"Yeni isimle at" means create a new file and preserve previous notes.
