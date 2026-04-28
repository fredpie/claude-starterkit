> Source : AI Automation Society - By Nate Herk

This guide summarize the key concepts, the WAT framework and the steps for building, testing and deploying with AI automations using Claude Code.

---

## The "WAT" Framework

A three-layer structure that separates probabilistic reasoning (AI) from deterministic execution (Code).

### Layer 1 : **W**orkflows (`/workflows`)

- **Formats :** `.md` (Markdown) files
- **Purpose :** SOPs (Standard Operating Procedures) - define the objective, required inputs, tool sequences and edge case handling in plain English (or french)
- **Analogy :** The "manager" telling the worker exactly waht steps to take

### Layer 2 : Agents (`claude.md`)

- **Formats :** `.md` system promt
- **Purpose :** Core instruction set for Claude Code - tells the agent how to navigate folders, which tools to use and how to follow the WAT framework
- **Self-Healing :** The agent is instructed to read errors, refactor tools and update workflow if a process fails

### Layer 3 : Tools (`/tools`)

- **Format :** `.py` (Python) files
- **Purpose :** Actual code that executes actions (scraping, emailing, database queries)
- **Security :** API keys and secrets are **never** stored in these files. We use `.env`

---

## Planning & Building automation

Before writing a single line of code, move into **Plan mode**.

1. **The Brain Dump :** Describe your goal clearly (e.g. "Scraping YouTube channels in the AI niceh and create a branded slide deck)
2. **Iterative Questioning :** In `Plan Mode`, the agent ask clarifying question about frequency, data points and delivery methods
3. **To-Do List :** Once the plan is accepted, the agent creates a checklist and executes it step-by-step (creating folders, writing code (Python or TypeScript), setting up workflows)

---

## Superpowers : MCP & Skills

**Claude Code** can be extended with external capabilities to handle task it can't do natively.

- **MCP (Model Context Protocol) Servers :** An "App Store" for AI. Provide a universal port to connect services like Gmail, Google Calendar, etc. without individual API integration.
- **Skills :** Dynamic, reusable instructions or custom prompts that Claude loads only when needed.
  - **Local Skills :** Installed for a specific project
  - **Global Skills :** Installed across your entire Claude Code instance for use in any project

### Skills vs Projects

- **Project** provide a static background knowledge always loaded when you start chat within them.
- **Skills** provide specialized procedure that activate dynamically when needed and work everywhere across Claude.

### Skills vs MCP

- **MCP** connects Claude to external services and data source (informations).
- **Skills** provide procedural knowledge - instructions for how to complete specific tasks or workflows.

**Use both together: MCP connections give Claude access to tools, while Skills teach Claude how to use those tools effectively.**

---

## Testing & Optimization

Building the automation is only half the baltle : you must test and refine the logic.

- **Initial Run :** Execute the workflow in a test environment to identify missing dependencies or API errors
- **Error Resolution :** If a tool fails, copy the terminal error and paste it back into Claude Code chat. The agent will analyze the log, fix the script and re-run the test.
- **Branding & Assets :** Drag and drop assets (logos, images, fonts) into your project folder and instruct the agents to incorporate them into final deliverables (PDFs, slide decks, etc.)

---

## Deploying to Production (Modal)

Once the automation works locally, host it in the cloud to run automatically on a schedule (CRON) or via a trigger (Webhook).

- **Hosting Platform :** Modal, Digital Ocean, Runpod
- **Benefits :** Pay only for the seconds the code is actually running
- **Deployment Steps :**
  1. Install the Modal Client via Claude Code
  2. Instruct the agent : "Push this workflow to Modal to run every Monday at 6 AM"
  3. **Security Review:** Always ask the agent to perform a security review before deploying to ensure no API keys or vulnerabilities are exposed
- **Monitoring:** Use the Modal dashboard to check logs and track execution history. If a cloud run fails, paste the Modal logs back into Claude Code to fix the deployment.
