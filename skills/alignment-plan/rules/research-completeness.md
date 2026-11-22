# Research completeness (before any plan is "ready for alignment")
Research is done only when every item below is done, each with its evidence (command, link, `file:line`, ticket, PR or document URL).

1. **Current sources.** Read the current version of every source the work touches: for code, `git fetch` and read from `origin/...` refs or the named branch, not a stale local checkout; for documents, the latest version. Report where a local copy is behind; don't switch or delete branches without asking.
2. **Related items.** The task itself, its parent and sibling tasks, linked items, comments, and recent changes to its description (a rewritten description changes the scope).
3. **Dependencies.** Everything unfinished the work builds on (open branches, PRs, drafts, decisions): its state and review status, and whether it still matches its own goal. The reference the task mirrors, if any.
4. **Conventions and reuse.** How the same thing is solved elsewhere in the project; whether it exists already or belongs in a shared place; relevant decisions and guides.
5. **How it will be checked.** Code: tests (red/green where the code is testable). Config, infrastructure or non-code work: the checks that prove it works. The plan states which and why.
6. **Open questions.** Research each one first. It stays open only if it is
   - a decision someone else must make (name who), or
   - blocked (name the source, what was tried, and what access is needed).
   Each open question lists what was researched, with sources. Never "I didn't investigate that".
7. **Freshness.** Directly before presenting, re-check the states of tasks, branches, PRs and builds, and label them "as of <date>".

**Wording.** Say "ready for alignment" only when items 1–7 are done. Otherwise say "Draft, research incomplete:" and list the missing items, then continue researching or ask only for the blocked access. Don't add solution ideas or requirements the user didn't ask for.
