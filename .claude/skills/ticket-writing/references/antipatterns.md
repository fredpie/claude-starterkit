# Ticket Anti-Patterns & Fixes

Use this file when reviewing an existing ticket to identify what's wrong and how to fix it.

---

## Anti-Pattern Catalog

### 1. Vague Title

**Signs:**

- "Fix bug", "Update UI", "Backend stuff", "New feature"
- No verb, no component, no context

**Fix:**
Apply the `[Scope] Verb + Noun + Context` format.

- ❌ `Fix login bug` → ✅ `[Auth] Fix session expiry not triggering logout on /dashboard`

---

### 2. Missing or Untestable Acceptance Criteria

**Signs:**

- No AC at all
- AC uses subjective language: "should be fast", "looks good", "handles errors"
- AC describes implementation, not outcome: "Use a useEffect hook to fetch data"

**Fix:**
Rewrite each AC as a testable Given/When/Then statement or a concrete pass/fail condition.

---

### 3. Ticket Scope Creep (Too Big)

**Signs:**

- Title mentions multiple features or systems
- Estimate is > 3 days
- AC list has > 10 items covering different concerns

**Fix:**
Split into sub-tickets. Promote to an Epic with child tickets.

---

### 4. Ticket Too Small (Nano-ticket)

**Signs:**

- Estimate is < 2 hours
- Single-line change with no context or risk

**Fix:**
Group with related chores. Add as a sub-task to a parent ticket.

---

### 5. No Business Context

**Signs:**

- "Context" section is empty or just says "we need this"
- Dev can't understand why this matters or who it's for

**Fix:**
Add one sentence explaining: who needs this, why now, and what breaks without it.

---

### 6. AC Describes Implementation Detail

**Signs:**

- "Call the `/api/v2/refresh` endpoint"
- "Use Redis to cache the response"
- "Add a useCallback around the handler"

**Fix:**
Rewrite the AC from the perspective of the behavior being tested, not the code being written.

- ❌ "Cache the response with Redis TTL 300s" → ✅ "Subsequent requests within 5 minutes return the same data without triggering a new API call"

---

### 7. Missing Error / Edge Cases in AC

**Signs:**

- Only the happy path is described
- No mention of: empty state, loading state, error state, unauthenticated user, rate limit, etc.

**Fix:**
For every AC covering the happy path, ask: "What happens if this fails? What if the data is empty?"
Add at least one error state criterion.

---

### 8. Undocumented Dependencies

**Signs:**

- Ticket requires a separate API, config value, or another ticket to be done first — but this isn't mentioned
- Dev starts work and gets blocked by something that could have been flagged

**Fix:**
Add a "Dependencies" or "Blocked by" section. Even "No known dependencies" is useful.

---

### 9. Undefined Definition of Done

**Signs:**

- No DoD at all
- PR opened with no tests, no QA, no review — and it gets merged anyway
- "Done" means different things to different people on the team

**Fix:**
Add a checklist with the team's standard DoD: code review, tests, staging QA, docs, monitoring.

---

### 10. Spike That Produces Code (not a decision)

**Signs:**

- Spike ticket ends with "implement the solution"
- Time box not specified
- No defined question to answer

**Fix:**
A spike must be time-boxed and produce a document or decision — not production code.
Create a follow-up feature ticket for the actual implementation.

---

## Quick Review Checklist

Use this to audit any ticket in < 2 minutes:

- [ ] Title is specific and actionable (verb + scope + context)
- [ ] Context explains the business reason
- [ ] At least 3 AC covering happy path, edge case, error state
- [ ] AC are testable (not subjective, not implementation-level)
- [ ] Estimate fits in 1–3 dev days (not too big, not too small)
- [ ] Dependencies are documented
- [ ] DoD is defined
- [ ] No ambiguous language ("fast", "good UX", "handle it", "as needed")
