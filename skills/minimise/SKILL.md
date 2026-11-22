---
name: minimise
description: Minimise a finished change before review - remove code, config, tests and docs the stated requirements don't need (speculative abstractions, unused options, extra logging, duplicate helpers, defensive checks for impossible cases, comments restating code), keep behaviour and tests green. Use when asked to "minimise", "reduce code bloat", "strip to the minimal version", "make this diff smaller".
argument-hint: "[branch, change or ticket]"
---

# Minimise

Precondition: the change works and its tests or checks pass.
Goal: the smallest change that still meets the stated requirements (acceptance criteria, the plan's minimal scope, or what the user asked for). Required behaviour stays; everything else goes.

## 1. Measure
For a git branch: `git diff --stat origin/<target>...HEAD` and note the totals (files, insertions, deletions) for the report. Otherwise note the size of the change.

## 2. Simplify
If the built-in `simplify` skill is available (Claude Code), run it on the change (reuse, simplification, efficiency).

## 3. Cut what the requirements don't need
Go through the change hunk by hunk. For each added or changed element ask: which requirement, test or plan step needs it? None → remove it. Typical candidates:
- abstractions, interfaces, parameters, config options or flags with a single use or none
- helpers that duplicate existing code in the repo or a shared library (reuse instead)
- logging, metrics, validation or null checks for cases that can't occur, unless a project rule requires them
- comments that restate the code; docs for behaviour that didn't change
- files touched only for formatting or unrelated cleanup (revert them)
- CI, deployment or config changes beyond what the verification needs

Never change or delete tests written to prove the requirements. Other added tests: keep only those that prove a requirement. If a cut would change required behaviour or a project rule asks for the element, keep it.

## 4. Commit and check
- In git: one commit with what was removed and why in the body, in the project's commit format. Nothing removed → no commit.
- Push if the work is on a pushed branch, then confirm the tests or CI are still green.

## 5. Report
```
Minimise: <files/+/- before> → <after>
Removed: <item – why not needed>
Kept although questionable: <item – which requirement/rule needs it>
```
