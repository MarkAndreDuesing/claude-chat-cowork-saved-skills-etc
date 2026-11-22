---
name: ticket-draft
description: Draft issue-tracker tickets (bugs, tasks, sub-tasks, parent tickets, tech-debt) from the user's template - title conventions, concrete example first, code path, evidence separated from theory, explicit scope, testable acceptance criteria. Use when asked to write, draft, split or rewrite a ticket, issue, bug report or sub-task in any tracker (Jira, GitHub, GitLab, Linear, ...).
argument-hint: "[what the ticket is about]"
---

# Ticket draft

Use `template.md` (next to this file). Pick the variant that fits:
- parent ticket or bug with sub-tasks → section 2
- operational / infrastructure problem → section 3 (Problem / Suggested solution)
- feature or logic change in one component → section 4 (Change paragraph + Acceptance criteria)
- bug report → section 5
- small sub-task whose parent carries the context → section 6

Follow the conventions in section 1 and run the checklist in section 7 before showing the draft.
Show the draft first; create the ticket in a tracker only after the user's OK.
The `communication` skill rules apply: only facts from the sources, unconfirmed causes marked as such.
