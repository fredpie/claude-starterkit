# Ticket Templates

---

## Feature Ticket

```
## [Scope] Title

**Type:** Feature
**Priority:** [P0 / P1 / P2 / P3]
**Estimate:** [XS / S / M / L / XL]
**Labels:** [frontend / backend / api / design / infra]

---

### Context / Why
> Why does this feature need to exist? What user or business problem does it solve?
> One paragraph max. Link to PRD, Figma, or relevant discussion if available.

---

### Description
> What needs to be built? High-level, no implementation details.

---

### Acceptance Criteria
- [ ] Given [context], when [action], then [outcome]
- [ ] Given [context], when [action], then [outcome]
- [ ] Edge case: [condition], then [outcome]
- [ ] Error state: [condition], then [outcome]

---

### Technical Notes *(optional)*
> Hints for the implementer. Keep it light — avoid over-specifying.
> - Suggested approach or relevant existing component
> - Known constraints (e.g. rate limits, schema constraints)
> - Do NOT implement X (explain what's out of scope)

---

### Dependencies
- Blocked by: [ticket-id or description]
- Requires: [env, config, data, API key, etc.]
- Related to: [ticket-id or PR link]

---

### Definition of Done
- [ ] Code reviewed and approved
- [ ] Unit/integration tests written and passing
- [ ] QA verified on staging
- [ ] Feature flag configured (if applicable)
- [ ] Documentation updated (if applicable)
- [ ] No new Sentry errors introduced
```

---

## Bug Ticket

```
## [Scope] Fix [what is broken] — [brief impact]

**Type:** Bug
**Severity:** [P0-Critical / P1-High / P2-Medium / P3-Low]
**Frequency:** [Always / Intermittent / Rare]
**Reported by:** [User / QA / Monitoring / Dev]

---

### Summary
> One-sentence description of the broken behavior and its impact.

---

### Steps to Reproduce
1. Go to [URL / screen]
2. [Do action]
3. [Do action]
4. Observe: [what happens]

---

### Expected Behavior
> What should happen according to specs or user expectations?

---

### Actual Behavior
> What is actually happening? Be specific.

---

### Environment
- **Env:** [production / staging / local]
- **Browser / Platform:** [Chrome 122 / iOS 17 / Node 20]
- **User role / state:** [e.g. authenticated admin, empty state]
- **Reproducible since:** [date or version if known]

---

### Evidence
> Screenshot, video, Loom, Sentry link, log snippet

---

### Acceptance Criteria
- [ ] The bug no longer occurs under the reproduction steps above
- [ ] Existing tests pass without modification
- [ ] [Additional regression test if warranted]

---

### Root Cause *(fill in during investigation)*
> Leave blank until dev investigates.

---

### Definition of Done
- [ ] Fix deployed to staging and verified
- [ ] Regression test added
- [ ] Root cause documented
```

---

## Chore / Tech Debt Ticket

```
## [Scope] [Refactor / Update / Remove / Migrate] [what] — [reason]

**Type:** Chore
**Priority:** [P1 / P2 / P3]
**Estimate:** [XS / S / M / L]

---

### Context / Why
> Why does this need to happen now? What breaks, slows down, or creates risk if we don't address it?
> Link to the original issue or debt tracking doc if available.

---

### Scope of Work
> What files, modules, services, or components are involved?
> What is explicitly OUT of scope?

---

### Acceptance Criteria
- [ ] [Behavior is preserved / tests still pass]
- [ ] [Specific measurable improvement, e.g. "No deprecated API calls remain in the codebase"]
- [ ] [Cleanup verified: no dead code, no TODO comments left]

---

### Definition of Done
- [ ] Code reviewed
- [ ] All existing tests pass
- [ ] No regression introduced
- [ ] PR description explains what changed and why
```

---

## Spike / Research Ticket

```
## [Spike] [Investigate / Evaluate / Prototype] [topic]

**Type:** Spike
**Time Box:** [4h / 1 day / 2 days — hard limit]
**Assigned to:** [name or TBD]

---

### Background
> What problem is this spike trying to solve? What decision does it enable?

---

### Questions to Answer
1. [Specific question this spike must answer]
2. [Specific question this spike must answer]
3. [Specific question this spike must answer]

---

### Deliverable
> What is the expected output at the end of the time box?
> Must be a document, decision, proof-of-concept, or recommendation — NOT production code.

Examples:
- A written comparison of [Option A] vs [Option B] with a recommendation
- A working prototype that demonstrates [specific capability]
- A decision record (ADR) signed off by the team

---

### Out of Scope
> What should NOT be produced by this spike?

---

### Definition of Done
- [ ] Time box respected (no overrun without explicit approval)
- [ ] Deliverable shared with team
- [ ] Follow-up tickets created if applicable
```

---

## Epic

```
## [Epic] [High-level initiative name]

**Type:** Epic
**Target:** [Sprint / Quarter / Release]
**Owner:** [name or TBD]
**Status:** [Discovery / Planned / In Progress / Done]

---

### Goal
> What business or product outcome does this epic deliver?
> One paragraph. No implementation details.

---

### Success Metrics
- [Measurable outcome 1, e.g. "Listing creation time < 2min end-to-end"]
- [Measurable outcome 2]

---

### Scope

**In scope:**
- [Feature or capability 1]
- [Feature or capability 2]

**Out of scope:**
- [Explicitly excluded work]

---

### Proposed Child Tickets
> These are starting points — not a final list. Will be refined during planning.

| # | Title | Type | Estimate |
|---|---|---|---|
| 1 | `[Scope] [Title]` | Feature | M |
| 2 | `[Scope] [Title]` | Feature | S |
| 3 | `[Scope] [Title]` | Chore | XS |
| 4 | `[Scope] [Title]` | Spike | 1d |

---

### Dependencies & Risks
- **Depends on:** [system, team, or ticket]
- **Risk:** [known unknowns or blockers]

---

### Definition of Done
- [ ] All child tickets completed and closed
- [ ] Success metrics validated
- [ ] Stakeholder sign-off received
```
