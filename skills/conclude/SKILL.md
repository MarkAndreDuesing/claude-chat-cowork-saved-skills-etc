---
name: conclude
description: Write the conclusion of the current session's task to the user's OneDrive Claude/notes/conclusions folder, so the outcome and its reasoning can be recreated later. Only when the user says the task is done and asks for it.
argument-hint: "[ticket or short task name]"
disable-model-invocation: true
---

> **Cloud sessions** (claude.ai/code) can't use this skill: they don't load `~\.claude\skills` and can't reach OneDrive.
> Workaround (tested 2026-11-02): in a local terminal run `claude --teleport`, pick the cloud session, then run `/conclude`
> in the teleported local copy. The original cloud session stays; archive it by hand in the Claude desktop app sidebar.

Write a conclusion of the task done in this session to the user's OneDrive folder `Claude/notes/conclusions/`:
- **Claude Code with a local OneDrive** (the folder exists locally, e.g. under `%OneDriveCommercial%` or `%OneDrive%`): write the file there.
- **Chat or Cowork** (no local folder): use the Microsoft 365 / OneDrive connector if one is connected. Find the folder
  (name `conclusions`, the one whose web URL ends in `/Documents/Claude/notes/conclusions` in the user's own OneDrive),
  list it to check for an existing file, then upload the file into it
  (replace only when updating that same task's file). If no connector is connected, say so and
  show the conclusion in the reply instead. If the session ID is not available, put the chat title instead.

Purpose: if this laptop and the session history are lost, someone (or a new Claude session) can understand
what was done, why, and redo it from this file alone. Record facts from this session only: what was
actually done and verified, not what was planned. Say plainly what was not done or not verified.

**File name:** `<YYYY-MM-DD>_<ticket key or topic>_<short-kebab-slug>.md` (use `$ARGUMENTS` if given).
If a conclusion for the same task already exists, update it in place instead of creating another.
If an alignment plan for the task exists in `..\plans\`, link it and set its `status` to `done` or `superseded`.

```markdown
---
task: <ticket key / title>
date: <YYYY-MM-DD>
repos: [<repos / folders touched>]
session: ${CLAUDE_SESSION_ID}
plan: <relative link to the plan, if any>
---
# <Title>

## Outcome                 <!-- 2-4 sentences: what is now true -->
## What was done           <!-- concrete changes: files, branches, PRs, commits, settings, with paths/links -->
## Key decisions and why   <!-- incl. options rejected and the user's preferences that drove them -->
## How to recreate         <!-- steps or commands to redo it from scratch on a new machine -->
## Not done / open         <!-- follow-ups, unverified parts, known caveats -->
```

Never include secrets, tokens, credentials or customer personal data; refer to where they live instead.
Be exhaustive: record every change, decision, reason, rejected option, command and open point from the session.
Completeness wins over brevity here; the length and writing rules of the `communication` skill don't apply, its facts rules do. Give the user the file path as a link.

**Then archive this session** (the user asked for this as part of `/conclude`):
1. Only in the Claude desktop app, i.e. when `mcp__ccd_session_mgmt__archive_session` is available (load it via ToolSearch
   if it is deferred). In a plain terminal session (including a teleported cloud session), skip
   this and end the closing message with: "Not archived: archiving is only available in the desktop app."
   In chat or Cowork, end with: "Not archived: move this chat to the 'Finished' group in the sidebar by hand."
   For a teleported session, add that the original cloud session can be archived from the desktop app sidebar.
2. Archiving removes the session's worktree. In the working directory and every repo or worktree this session changed, run
   `git status --porcelain` and `git log @{u}..` (or check whether a branch has an upstream at all). If anything is
   uncommitted, unpushed or has no upstream, do not archive: list what is pending and stop.
3. Otherwise, write the closing message first (the conclusion link, plus "archiving this session now"), then call
   `archive_session` with `session_id: "self"` and `reason: "Task concluded"` as the very last action. The conversation ends there.
