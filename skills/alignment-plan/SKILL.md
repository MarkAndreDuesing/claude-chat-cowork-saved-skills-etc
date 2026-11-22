---
name: alignment-plan
description: Write or update the human-review alignment plan for the current task in the user's OneDrive Claude/notes/plans folder. Use when the user asks for an alignment plan / plan for review after a task has been researched and planned.
argument-hint: "[ticket or short task name]"
---

Write the alignment plan for the task researched in this session to the user's OneDrive folder `Claude/notes/plans/`:
- **Claude Code with a local OneDrive** (the folder exists locally, e.g. under `%OneDriveCommercial%` or `%OneDrive%`): write the file there.
- **Chat or Cowork** (no local folder): use the Microsoft 365 / OneDrive connector if one is connected. Find the folder
  (name `plans`, the one whose web URL ends in `/Documents/Claude/notes/plans` in the user's own OneDrive),
  list it to find an existing file for this task, then upload the file into it
  (replace only when updating that same task's file). If no connector is connected, say so and
  show the plan in the reply instead. If the session ID is not available, put the chat title instead.

Only write it once the research is done as defined in `rules/research-completeness.md` (next to this file); otherwise mark it "Draft, research incomplete:" with the missing items. If something could not be checked (blocked access, missing info),
say so in the plan as an open question instead of guessing. Do not add ideas or requirements the user did not ask for.

**File name:** `<ticket key or topic>_<short-kebab-slug>.md`, e.g. `PROJ-123_short-topic.md`
(use `$ARGUMENTS` if given). One file per task: if it already exists, read it and update it in place
(bump `updated`) rather than creating a new file.

**Content** (concise, written for a colleague who has not seen this session):

```markdown
---
task: <ticket key / title>
status: draft | in review | approved | done | superseded
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
repos: [<repos or folders touched>]
session: ${CLAUDE_SESSION_ID}
---
# <Title>

## Goal
## Context and findings      <!-- what was researched, with sources: files, tickets, commits, docs -->
## Proposed approach         <!-- steps in order, per repo or area; merge order if several repos -->
## Alternatives considered   <!-- only real ones, one line each with why not -->
## Risks and open questions  <!-- incl. anything that could not be verified -->
## Decisions needed from reviewers
```

Never include secrets, tokens, credentials or customer personal data.
Finish by giving the user the file path as a link.
