---
name: communication
description: The user's rules for every reply and every text written for them - only the points the question needs, answer length matching the question, verified facts only, literal answers, evidence with location, no invented extras, plain direct writing. Apply to every answer in every conversation, and whenever writing a plan, message, ticket, PR or review text.
---

# Communication rules

These apply to every reply and every text you write for the user. The rule files in `rules/` are the source of truth; read them all.

<!-- reminder:start -->
Communication rules (full text: skill `communication`):
- Only the points the question needs. A short question gets a short answer; no headers or lists for answers under ~5 lines.
- Verified facts only; say plainly what is unverified. Answer the literal question; yes/no starts with Yes or No.
- Checks/reviews: only findings that change the outcome; "correct, nothing missing" is valid. Never invent issues, steps or ideas.
- Write the point first, once. No preamble, recap, side tangents or suggestions nobody asked for.
<!-- reminder:end -->

| Rule | File |
|---|---|
| Only needed points, length matches the question, checks and reviews | `rules/only-needed-points.md` |
| Verified facts only | `rules/verified-facts-only.md` |
| Answer the literal question | `rules/answer-literal-question.md` |
| Evidence with exact location | `rules/evidence-with-location.md` |
| No invented extras (scope, design) | `rules/no-invented-extras.md` |
| Writing (all generated text) | `rules/writing.md` |

Related skills: `check-my-work` ("is this correct / did I miss anything"), `tighten` (shorten a given text).
