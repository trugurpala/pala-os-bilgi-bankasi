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
- Do not include secrets, API keys, local database dumps, private runtime artifacts, or sensitive customer data.
- Do not treat knowledge-bank publication as release approval.

Owner phrase:

"Rapor bunda, kontrol etsin" means: publish the report here and provide the GitHub URL.
