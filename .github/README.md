# personal – Claude skills for Chat, Cowork and Claude Code

A plugin marketplace with one plugin, `personal`.

| Skill | What it does | Loads |
|---|---|---|
| `communication` | Rules for every reply and written text: only the needed points, verified facts only, literal answers, evidence with exact location, no invented extras, plain direct writing | on trigger |
| `explain` | Explains code, changes, concepts or a process in plain language, at the requested granularity (step-by-step, line-by-line, file-by-file, from the ground up, …) | on trigger |
| `check-my-work` | Checks work you describe or show; gives a verdict and only the findings that change the outcome | on trigger |
| `tighten` | Shortens and sharpens a text without losing content | on trigger |
| `alignment-plan` | Writes a plan for human review to `Claude/notes/plans` in your OneDrive, after a research-completeness checklist | on trigger |
| `conclude` | Writes an exhaustive conclusion of a finished task to `Claude/notes/conclusions` in your OneDrive, so it can be redone later | manual (`/conclude`) |
| `minimise` | Cuts a finished change down to what the stated requirements need, keeping tests green | on trigger |
| `coding-rules` | Coding and git rules: think first, simplest code, surgical changes, comments, safe operations, ask once before git writes, never merge protected branches, commit hygiene | on trigger |
| `ticket-draft` | Drafts issue-tracker tickets (bugs, tasks, sub-tasks) from a template | on trigger |
| `design-doc` | Writes a design document for a feature or change from a template | on trigger |

`alignment-plan` and `conclude` save through a OneDrive / Microsoft 365 connector when one is connected; otherwise they show the text in the reply.

## Install in the Claude desktop app

1. Open the plugins page: **Customize → Plugins** (in Cowork: **Customize → Browse plugins → Personal**).
2. Select **Add** (or **+**) → **Add marketplace**, and choose to add it from GitHub.
3. Enter `MarkAndreDuesing/claude-chat-cowork-saved-skills-etc`.
4. Add the plugin **personal** from that marketplace.

Repeat in each Claude account. Menu labels can differ between app versions.
