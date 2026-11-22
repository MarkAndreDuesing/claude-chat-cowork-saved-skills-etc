---
name: explain
description: Explain code, changes, concepts or a process in plain language with code snippets. Use when the user asks to "explain", "break down", "in layman's terms", "with code snippets", "step-by-step", "line-by-line", "file-by-file", "class-by-class", "method-by-method", "section-by-section", "from the ground up", "assume I'm a beginner", "elaborate on", "what does X mean", "what is the difference between", "what does X do" or "what is done at each stage".
argument-hint: "[what to explain] [from the ground up | step-by-step | ...]"
---

# Explain

The `communication` skill rules apply in full, especially `only-needed-points.md` and `verified-facts-only.md`. Read the code or source before explaining it; never explain from memory.

## Always, in this order
1. **Answer first.** Open with the direct answer to the question, before terms or code.
2. **Terms.** Define, in plain words, only the terms the answer uses. Define each term once, where it first appears.
3. **Code snippets** with their exact location: repository, branch or commit when relevant, `file:line`, and the named class, method, stage or section.
4. **Full sentences.** No analogies, history or extra walkthroughs unless asked.

## Structure by requested granularity

| Phrase | Structure |
|---|---|
| step-by-step | Numbered steps in execution order. For each step: what happens, which code does it, what it produces for the next step. |
| line-by-line | Every line or line group in order, with its line numbers: what it does and why it is needed. |
| file-by-file | One heading per file (full path). Inside: the parts that matter and why the file is needed. |
| class-by-class | One heading per class: its responsibility, its fields/state, how other classes use it. Methods only briefly. |
| method-by-method | One heading per method (`Class.method`, `file:line`): inputs, what it does in order, output or side effects, who calls it. |
| section-by-section | One heading per section (config block, pipeline stage, template block, document heading): what it does and why. |
| from the ground up / assume I'm a beginner | Short answer first. Then the goal or problem before the mechanics. Then the concepts in dependency order, each built only on concepts already explained. Assume no background: basic terms of the field are defined too. |
| elaborate on X / what does X mean | Only X, in this order: what X is, what it does for us (why it is needed), how we do it step by step with code and `file:line`. |

- Combined requests nest from coarse to fine, e.g. "file-by-file, section-by-section" means file headings with their sections inside.
- For changes (diffs, PRs), explain what changed (before and after where useful) and why each change is needed.
- "Layman's terms" changes only the wording (plain words, every needed term defined), not the scope: still only what was asked.
