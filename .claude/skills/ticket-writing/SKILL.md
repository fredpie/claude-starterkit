---
name: ticket-writing
description: >
  Generate well-structured, actionable development tickets (features, bugs, chores, spikes, epics) following
  engineering best practices. Use this skill whenever a user wants to write, improve, or review a development
  ticket, user story, issue, or task — even if they only give you a rough idea or a one-liner. Also trigger
  when a user says things like "help me write a ticket", "create a Jira/Linear/GitHub issue", "turn this
  into a ticket", "my ticket is missing something", or "review my acceptance criteria". If a user describes
  a feature, bug, or technical task and it sounds like it could be a development ticket, use this skill.
---

# Effective Ticket Writing for Development Teams

This skill produces high-quality, handoff-ready development tickets from any level of user input —
from a rough one-liner to a detailed brain dump. The output should allow any developer on the team
to start working without asking questions.

---

## Workflow

### Step 1 — Gather context

Before generating a ticket, identify:

1. **Ticket type** — Feature, Bug, Chore/Tech Debt, Spike, or Epic
2. **Raw input** — What the user described (requirement, bug description, idea, etc.)
3. **Scope/product area** — Frontend, Backend, API, Infra, Design, etc. (if mentioned)
4. **Target platform** — (e.g. Linear, Jira, GitHub Issues, Notion — affects formatting)

If the ticket type is ambiguous, infer it from context. If completely unclear, ask one focused question before proceeding.

---

### Step 2 — Select the template

Route to the correct template from `references/templates.md` based on ticket type:

| Type        | When to use                                                      |
| ----------- | ---------------------------------------------------------------- |
| **Feature** | New functionality, user-facing or internal                       |
| **Bug**     | Something is broken or behaving incorrectly                      |
| **Chore**   | Refactor, dependency update, CI, non-feature dev work            |
| **Spike**   | Research or exploration with a time-boxed deliverable            |
| **Epic**    | Large initiative that needs to be broken down into child tickets |

---

### Step 3 — Generate the ticket

Apply the template, then fill in each section using the user's input + your own reasoning.

**Non-negotiable fields** (every ticket must have these):

- A sharp, actionable **title** (see Title Rules below)
- A clear **Context / Why** (even one sentence)
- At least one **Acceptance Criterion** (see AC Rules below)

**Infer what you can** — don't leave fields blank with "N/A" just because the user didn't mention them. Use reasonable defaults based on context. Flag anything that genuinely needs input from the user.

---

### Step 4 — Output and review

Present the full ticket in a clean, readable format.

After the ticket, add a **"Notes"** section of max 5 bullets — terse, one line each. Only include:

- Assumptions you made that the user should validate
- A blocking unknown the dev cannot resolve alone
- Edge cases not covered by the AC
- A scope assumption the user should confirm
- Missing information that could block a developer
- Suggestions to improve scope, split the ticket, or add sub-tasks
- A split suggestion if the ticket clearly exceeds 3 dev days

**Skip the Notes section entirely if there's nothing worth flagging.**

---

### Step 5 — Save to file

Save the ticket as a markdown file and share it with the user:

- **Path:** `docs/tickets/[ticket-slug].md`
- **Slug:** lowercase, hyphens, no brackets — derived from the title. Ex: `fms-ui-implement-fleet-crud.md`
- Content: exact same markdown presented to the user
- Use the `present_files` tool to give the user a download link

---

### Step 6 — Generate the Plan prompt

After saving the ticket, generate a **Plan prompt** ready to be pasted into a coding agent (Cursor, Claude Code, etc.).

The prompt must instruct the agent to:

1. Read the ticket and explore the relevant codebase **before** proposing anything
2. Produce a structured plan (files to create, files to modify, execution order)
3. **Stop and wait for approval** before writing any code
   Template:

\`\`\`

## Plan Task — [ticket title]

Read the following ticket carefully, then explore the codebase to understand the current structure before proposing anything.

--- TICKET ---
[paste full ticket content here]
--- END TICKET ---

Your task is to produce a plan — not to write code yet.

The plan must include:

- List of files to create (with proposed path and responsibility)
- List of files to modify (with a short description of what changes)
- Execution order (what gets built first and why)
- Any ambiguity or blocking unknown that would prevent implementation
  Do not write any code. Output the plan, then stop and wait for approval.
  \`\`\`

Fill in the ticket content and save the prompt as `docs/tickets/[ticket-slug].plan.md`.
Present both files to the user together.

---

## Title Rules

Format: `[Scope] Verb + Noun + Context`

- Start with an action verb: Add, Fix, Implement, Refactor, Remove, Update, Migrate, Expose
- Include the affected component or area
- Be specific enough to distinguish from other tickets
- Keep under ~80 characters
  **Good examples:**
- `[API] Add pagination to GET /properties endpoint`
- `[FE] Fix broken layout on PropertyCard at mobile breakpoint`
- `[Infra] Migrate Redis config to environment-based secrets`
- `[Auth] Implement refresh token rotation on session expiry`
  **Bad examples:**
- `Fix bug` — too vague
- `Update the thing` — meaningless
- `Backend changes for new feature` — no action, no scope

---

## Acceptance Criteria Rules

Each AC must be:

- **Testable** — can be verified as pass/fail
- **Outcome-oriented** — describes what happens, not how to implement it
- **Unambiguous** — no subjective terms like "fast", "intuitive", "simple"
- **Self-contained** — one condition per criterion
  **Preferred format:** `Given [context], when [action], then [outcome]`

Or simple bullet format: `The [actor] can [do X] when [condition]`

Every ticket should cover:

- ✅ Happy path (main success scenario)
- ✅ At least one edge case or boundary condition
- ✅ Error/failure state (if applicable)
  **Good AC:**

```
- Given a valid session, when the user navigates to /dashboard, they see their property list
- Given more than 20 results, pagination controls appear and function correctly
- Given an expired token, the user is redirected to /login with an error message
```

**Bad AC:**

```
- The page loads fast ❌ (not testable)
- Good UX for the form ❌ (subjective)
- Handle errors ❌ (too vague)
```

---

## Ticket Sizing Guidelines

| Size     | Duration   | Approach                   |
| -------- | ---------- | -------------------------- |
| Sub-task | < 2h       | Group into a parent ticket |
| Task     | 0.5–3 days | Ideal ticket size          |
| Epic     | > 3 days   | Must be broken down        |

If the user's input describes something that spans more than ~3 dev days, generate an **Epic** structure with proposed child ticket titles rather than one giant ticket.

---

## Reference Files

Load the relevant reference file when generating tickets:

- `references/templates.md` — Full templates for all ticket types (Feature, Bug, Chore, Spike, Epic)
- `references/antipatterns.md` — Common mistakes and how to fix them (load when reviewing an existing ticket)
