# Ticket template

## 1. Conventions for every ticket

### Title
- **Sub-tasks:** `<Component>: <what changes> – <narrowing qualifier>`
  - Component prefix = the repo, service or area it lands in.
  - En dash (`–`) separates the topic from the specific angle.
    Example: `API: Connection-pool limit – release the DB connection during file upload`
  - Append `(optional)` for nice-to-have sub-tasks.
- **Bugs:** name the observed symptom, not the fix.
- **Parent tasks:** plain outcome statement, no component prefix.

### Formatting
- Section labels are **bold paragraphs**, not headings (`**Problem**`, `**Acceptance criteria**`).
- Sentence case for labels ("Acceptance criteria", not "Acceptance Criteria").
- Bullets, nested one level for breakdowns.
- Backticks for everything code-like: classes, `Class#method`, files, config keys, enum values, field paths,
  branch names, commit hashes, metric names.
- Short declarative sentences. No filler.
- Absolute dates ("changed to `medium` on 2026-09-30").
- Quote code only when it proves the point: a short excerpt with the line number.

### Content habits
- **Concrete example first:** the specific field, document or case where it went wrong.
- **Name the code path:** entry point → where the value is produced (`Controller.method(...)` → `Dto.field` → …).
- **Separate evidence from theory:** label unconfirmed causes explicitly
  ("Potential (not confirmed) source … working theory based on reading X, not yet confirmed against live behaviour").
- **Point to existing patterns** instead of inventing one ("mirroring the existing `XyzStrategy` pattern").
- **Proposals, not mandates:** "Suggested solution", "A potential proposed shape is…".
- **Explicit boundaries:** out of scope, blocked-on and "optional" are stated, not implied.
- **Why tests didn't catch it** (for bugs) and how a test will catch it next time.
- **Constraints reviewers must not miss:** personal data (e.g. no file names or IPs in logs), unknowns about the
  production environment, shared changes affecting other use cases.
- Attach: screenshots (before/after for UI), config files, handoff notes, links to example PRs.

---

## 2. Parent ticket / bug (umbrella with sub-tasks)

One dense summary paragraph, then details, then outcome-level acceptance criteria.

```
<One paragraph, in this order:>
- What is wrong, in one sentence (symptom in the system's terms).
- The reported case: concrete field / document / input → wrong result vs. expected.
- What already works (so nobody re-fixes it).
- Root cause: why the working part is defeated.
- Spread: where else the same pattern exists.
- Why tests don't catch it.
- Scope sentence: "This ticket <does A and B>; <X> and <Y> are out of scope."

**Details**

How <mechanism> works today (commits `<hash>`, `<hash>`):

* `<Class>.<method>` does <step 1>.
* <step 2>.
* `<file>` says:

    <short code excerpt with line number>

**Acceptance criteria**

* <Observable behaviour for the reported case, incl. the field that proves it>.
* <General rule that must hold everywhere, not just for the reported case>.
* A test fails if <the thing> drifts again.
```

Sub-tasks are then split per component / per concern, typically:
code change(s) → test/data alignment → optional observability.

---

## 3. Sub-task – variant A: "Problem / Suggested solution"

Use for operational, infrastructure or production issues.

```
**Problem**

* <What fails or can't be done, with the concrete symptom (log message, status)>.

    * <sub-symptom 1>.
    * <sub-symptom 2>.

* <Mechanism: which method holds/does what, with numbers (pool size 10 → 11th waits, fails after 30s)>.
* Reproduced locally with <exact setup>: <what failed>.
* <Why an existing attempt / branch `<branch>` is insufficient>.
* <Known unknowns>.

**Suggested solution**

* <Main change, referencing an existing pattern to copy>:

    1. <step 1>;
    2. <step 2>;
    3. <step 3>.

* <Secondary change(s)>.
* <Constraint: what must NOT be done / logged>.
* Add <test type> asserting <invariant>. Existing tests must stay green.
* Verify with <the local reproduction>: <expected observation>.
* (Optional:) <precondition that makes this worth doing>.
```

---

## 4. Sub-task – variant B: "Change paragraph + Acceptance criteria"

Use for feature or logic changes within one component.

```
<One paragraph:>
<Imperative goal sentence: "Make X take precedence over Y in Z.">
<Current state: what `Class`/`file` does today and the concrete consequence.>
<The change, file by file / section by section, naming fields and paths.>
<Proposed shape if non-obvious: "A potential proposed shape is <interface> with one implementation per
 <dimension>, mirroring <existing pattern>.">
<Side effects: "The `<file>` change applies to both use cases.">

**Explicitly out of scope:** <adjacent work that someone might assume is included>.

**Blocked on <area>:** <dependency>; <which part can proceed anyway>.

**Acceptance criteria**

* <Output / API response contains …>.
* No <anti-pattern> remains in `<file>`.
* With <input A> and <input B> in the same run, `<field>` comes from <A>.
```

---

## 5. Bug report (standalone or sub-task)

```
**Summary**
When <precondition>, <field/behaviour> (shown in <UI location>) is <wrong>. If <variation>, it works
correctly and <evidence of what "correct" looks like>.

**Steps to reproduce**

1. <Action with concrete input>.
2. <Navigate to …>.
3. Observe <column / field>.
4. Repeat with <variation> to compare.

**Expected result**
<One sentence covering all variations>.

**Actual result**

* <Variation 1>: <result>.
* <Variation 2>: <result>.

**Relevant code path**
`<Controller.method(...)>` → `<Dto.field>` → sourced from `<Entity.field>`.

**Potential (not confirmed) source**
<Where the value is written, which paths reach it, why this case is skipped.>
This is a working theory based on reading `<Class.method(...)>`, not yet confirmed against live behaviour.

**Scope / impact**
<Cosmetic vs functional, who sees it, how it hurts their workflow.>

<Screenshots: input + output for failing and working case.>
```

---

## 6. Lightweight sub-task (one-liner)

Fine when the parent carries the context (cloned series, per-repo chores).

```
<Imperative verb> <what> in `<file/component>` so that <outcome>, <constraint or example>.
e.g. <link to the reference PR(s) to replicate elsewhere>
```

---

## 7. Checklist before submitting

- [ ] Title has a component prefix (sub-task) or symptom wording (bug)
- [ ] Concrete reported case named (field, document type, use case, environment)
- [ ] Code path / classes / files in backticks
- [ ] Confirmed facts vs. working theory clearly separated
- [ ] Reproduction is exact (inputs, counts, timings, local setup)
- [ ] Out of scope / blocked-on / optional stated
- [ ] Acceptance criteria are observable and testable; one criterion guards against regression
- [ ] Test expectation stated ("existing tests stay green", new test asserts …)
- [ ] Personal-data and production-environment constraints mentioned where relevant
- [ ] Attachments: screenshots, config, reference PRs, handoff notes
