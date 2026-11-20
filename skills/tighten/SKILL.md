---
name: tighten
description: Shorten and sharpen a given text without losing content - remove filler, repetition, preamble, recaps, hedges and side tangents, keep every fact and the structure. Use when asked to "tighten", "shorten", "make this concise", "cut the fluff", "less wordy", "improve the prose" of a text, message, ticket, PR description, plan or doc.
argument-hint: "[text, file or what to tighten]"
---

# Tighten

Apply `communication/rules/writing.md` and `communication/rules/only-needed-points.md` to a text that already exists.

## Keep
- Every fact, number, name, link, path, command, decision and open question.
- The author's structure and headings, unless they repeat each other.
- The meaning. If a cut would change it, keep the sentence.

## Cut
- Preamble, restated questions, closing summaries and recaps.
- Repetition: a point said again in another section.
- Filler words and phrases, hedges on checkable claims, throat-clearing ("It's worth noting that").
- Side tangents and ideas the text's purpose doesn't need. If unsure whether something is a tangent, keep it and list it under "Possibly cut".

## Rewrite
- Point first, one point per sentence, active voice, plain words.
- Lists for parallel items; prose for reasoning.

## Output
The tightened text, ready to paste or written back to its file. Then, only if any: "Possibly cut:" with the sentences you kept but doubt.
Don't apply to conclusions (skill `conclude`): they are exhaustive on purpose.
