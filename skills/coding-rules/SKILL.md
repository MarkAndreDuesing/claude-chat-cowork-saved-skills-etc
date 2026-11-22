---
name: coding-rules
description: The user's rules for writing and changing code and for git - think before coding, simplest code first, surgical changes, comments, safe file operations, ask once before git writes, never merge protected branches, commit hygiene. Apply whenever writing, editing or reviewing code, or before any commit, push or pull request. Rules 1-3 of guardrails and the safe-operations rules also apply to edits of documents.
---

# Coding rules

These apply to every code change and every git action. The rule files in `rules/` are the source of truth; read them all.

| Rule | File |
|---|---|
| Think first, simplicity, surgical changes | `rules/guardrails.md` |
| Code comments | `rules/comments.md` |
| Safe file and environment operations | `rules/safe-operations.md` |
| Ask once before git writes | `rules/permission-gate.md` |
| Never merge protected branches | `rules/never-merge.md` |
| Commit hygiene | `rules/commit-hygiene.md` |
