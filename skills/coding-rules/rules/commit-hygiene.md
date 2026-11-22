# Commit hygiene
- One logical change per commit, independently revertible.
- Never mix formatting, refactoring and behaviour changes in one commit. Stage partially with `git add -p`.
- Run `git diff --check` before committing.
