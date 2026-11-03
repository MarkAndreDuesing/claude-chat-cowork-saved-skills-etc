---
name: alignment-plan
description: Write or update the human-review alignment plan for the current task in OneDrive\Claude\notes\plans. Use when the user asks for an alignment plan / plan for review after a task has been researched and planned.
argument-hint: "[ticket or short task name]"
---

Write the alignment plan for the task researched in this session to OneDrive `Claude/notes/plans/`:
- **Claude Code on the laptop** (the folder exists locally): write the file to
  `%OneDriveCommercial%\Claude\notes\plans\`.
- **Chat or Cowork** (no local folder): use the Microsoft 365 connector. Find the folder with `sharepoint_folder_search`
  (name `plans`, pick the one whose webUrl ends in `/Documents/Claude/notes/plans` in the user's own OneDrive),
  list it with `read_resource` to find an existing file for this task, then `sharepoint_upload_file` into it
  (`conflictBehavior: "replace"` only when updating that same task's file). If the connector is not connected, say so and
  show the plan in the reply instead. `${CLAUDE_SESSION_ID}` is not available there; put the chat title instead.

Only write it once the research is done. If something could not be checked (blocked access, missing info),
say so in the plan as an open question instead of guessing. Do not add ideas or requirements the user did not ask for.

**File name:** `<Jira key or repo>_<short-kebab-slug>.md`, e.g. `PROJ-123_short-topic.md`
(use `$ARGUMENTS` if given). One file per task: if it already exists, read it and update it in place
(bump `updated`, keep a short `## Revisions` log at the end) rather than creating a new file.

**Content** (concise, written for a colleague who has not seen this session):

```markdown
---
task: <Jira key / title>
status: draft | in review | approved | done | superseded
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
repos: [<repos touched>]
session: ${CLAUDE_SESSION_ID}
---
# <Title>

## Goal
## Context and findings      <!-- what was researched, with sources: files, tickets, commits, docs -->
## Proposed approach         <!-- steps in order, per repo; merge order if cross-repo -->
## Alternatives considered   <!-- only real ones, one line each with why not -->
## Risks and open questions  <!-- incl. anything that could not be verified -->
## Decisions needed from reviewers
```

Never include secrets, tokens, credentials or customer personal data.
Finish by giving the user the file path as a link.
