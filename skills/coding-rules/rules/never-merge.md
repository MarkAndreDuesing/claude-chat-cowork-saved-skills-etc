# Never merge protected branches
- Merging into remote `main`/`master`/`development`/`release/*` is the user's job only: no PR/MR merge, no auto-merge, no push to those branches.
- Local merges are allowed: `git pull` / `git merge origin/<branch>` to bring the remote into a local branch (including `origin/main` into a feature branch) and resolving the merge conflicts. A local protected branch only takes its own remote (`origin/main` into `main`), never another branch. The result is pushed to feature branches only.
- Never approve or request changes on PRs.
