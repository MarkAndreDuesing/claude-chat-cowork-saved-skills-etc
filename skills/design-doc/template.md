# Feature Design: <Feature Name>

| Field            | Value                        |
|------------------|------------------------------|
| Author           | <name>                       |
| Date             | <YYYY-MM-DD>                 |
| Related ticket   | <key / link>                 |
| Status           | Draft / In Review / Approved |
| Design call date | <YYYY-MM-DD or TBD>          |

---

## 1. Summary

One or two sentences: what the feature or change is and why it's needed (value, problem being solved).

---

## 2. Affected Areas

Every module, service or domain the change touches. For each: **what changes** and **why**. Flag new
communication between them (events, APIs) explicitly.

| Area / Service | Change summary | New communication between areas? |
|----------------|----------------|----------------------------------|
|                |                |                                  |

- [ ] All affected areas are identified.
- [ ] Module boundaries are respected (no direct data or database coupling across them).
- [ ] New or changed events are listed with their schema.
- [ ] New or changed public APIs are listed, including the impact on their consumers.

---

## 3. Feature Design

Enough detail that someone can start implementing after the call.

### 3.1 Current Behaviour

What happens today (if this changes existing behaviour). Diagrams or screenshots if helpful.

### 3.2 Proposed Behaviour

What should happen afterwards. Happy path first, then important variations.

### 3.3 Design / Architecture

- High-level approach (new classes or modules, sequence of calls, state transitions).
- Data model changes (tables, columns, migrations).
- API changes (new or changed endpoints or events).
- Diagrams (sequence, C4, state): link or embed.

### 3.4 Edge Cases & Error Handling

Known edge cases and error conditions and how they are handled (validation errors, missing data, timeouts,
concurrent updates, …).

### 3.5 Alternatives Considered

Alternatives and why they were rejected. Link a decision record if the choice is architecturally significant.

### 3.6 Open Questions

Questions to resolve in the call. This is the main agenda.

- [ ] Question 1
- [ ] Question 2

---

## 4. Automated Test Coverage

### 4.1 Unit Tests

| Class / Logic | Scenario (given/when/then) |
|---------------|----------------------------|
|               |                            |

### 4.2 Integration Tests

| Test type (service / controller / repository / listener) | Scenario (given/when/then) |
|-----------------------------------------------------------|----------------------------|
|                                                           |                            |

### 4.3 Contract Tests

If a new or changed API or event is consumed elsewhere: the contract test impact.

### 4.4 Non-Functional / Other Automated Checks

Performance, security or resilience tests needed.

---

## 5. Manual Test Plan

Specific enough that someone unfamiliar with the feature can follow it.

### 5.1 Preconditions / Test Data

Setup, test data, feature flags or configuration needed before testing.

### 5.2 Manual Test Steps

| # | Step | Expected Result |
|---|------|-----------------|
| 1 |      |                 |

### 5.3 Negative / Edge Case Scenarios

| # | Scenario | Expected Result |
|---|----------|-----------------|
| 1 |          |                 |

### 5.4 Cross-Team Verification

Who else needs to verify on their side, and how.

---

## 6. Rollout & Observability

- Feature flag needed? Yes/No — name.
- Migration steps (database, configuration, identity provider).
- New monitoring or alerting.
- Rollback plan.

---

## 7. Checklist Before the Design Call

- [ ] Affected areas identified and cross-area impacts called out.
- [ ] Proposed design documented (happy path, edge cases, alternatives).
- [ ] Automated test plan drafted.
- [ ] Manual test plan drafted with concrete steps.
- [ ] Open questions listed.
- [ ] Shared with all attendees at least one working day in advance.
