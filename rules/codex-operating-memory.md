# Codex Operating Memory

Owner directive:

When Codex produces a Pala OS report or performs meaningful local mutations in a Pala OS repo, Codex must also publish a concise report to this knowledge-bank repo and give the owner the GitHub link.

Default behavior:
- Repo: `trugurpala/pala-os-bilgi-bankasi`
- Visibility: public
- Report format: dated Markdown under `reports/<source-repo>/`
- Include: source repo, phase, changed files, new files, evidence commands, status, rollback note, and release posture.
- Always include a changed-files section. For implementation reports, add a separate changed-files manifest when there are multiple files or any pre-existing dirty files.
- Separate included files from excluded/pre-existing dirty files so the owner can review the mutation package quickly.
- For meaningful local mutations, publish a repo-change review package too: included files, excluded dirty files, new files, tracked diff stat, file-by-file change notes, evidence commands, and a raw patch/diff file when practical.
- If a tracked file includes older dirty changes, say that clearly and isolate the current phase intent from the full local diff.
- Reports are append-only by default: do not overwrite old report files. Use a new dated filename, and add `-v2` or an addendum suffix when publishing another report for the same phase.
- Corrections should be new correction/addendum files unless the owner explicitly asks to edit an existing report.
- Do not include secrets, API keys, local database dumps, private runtime artifacts, or sensitive customer data.
- Do not treat knowledge-bank publication as release approval.

Owner phrase:

"Rapor bunda, kontrol etsin" means: publish the report here and provide the GitHub URL.
