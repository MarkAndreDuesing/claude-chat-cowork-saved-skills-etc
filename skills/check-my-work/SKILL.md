---
name: check-my-work
description: Check work the user did and describes or shows ("here is what I did, is this correct?", "did I miss anything?", "did I forget anything?", "any errors?", "sanity check this", "does this look right?"). Gives a verdict and only the findings that change the outcome; "correct, nothing missing" is a valid result.
argument-hint: "[what to check]"
---

# Check my work

The `communication` skill rules apply in full. The aim is a verdict the user can act on, not a list to fill.

## 1. Establish the goal
- Take the goal from the user's words (what they were trying to achieve). If it isn't stated and several readings change the verdict, ask in one line.
- Check against that goal only, not against a fuller process you could imagine.

## 2. Check
- Read the actual material (commands, output, files, diff, config, text) before judging. Verify each suspected problem against its source; drop it if it doesn't hold.
- A finding qualifies only if it changes the outcome:
  - something is wrong (wrong fact, bug, a step that fails or does something other than intended)
  - something required for the goal is missing
  - a step causes damage or risk the user would not accept (data loss, security, cost)
- Not findings: style preferences, best practice in general, alternative ways that also work, extra steps "for safety" without a concrete failure they prevent, procedures the goal doesn't need.

## 3. Answer
```
<Correct. | Correct, with N issues: | Not correct: N issues:>
1. <what is wrong or missing> – <evidence/location> – <fix>
```
- No findings: answer "Correct, nothing missing." and stop. Add nothing else.
- Unverifiable parts: one line each, saying what could not be checked and why.
- Optional improvements: only when the user asked for them, otherwise at most one line marked "optional".
