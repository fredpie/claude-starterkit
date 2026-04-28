# Token Management Hacks

> Source : AI Automation Society

---

## What is a "Tokens" & How they actually worked ?

A token is the smallest unit of text that an AI model reads and charges you for : roughly one token per word.
Every time you send a message, Claude re-reads the entire conversation from the beginning. Message 1, its reply, message 2, its reply... all the way to your latest prompt. Every. Single. Time.

**Cost compounds, not adds.** Message 1 might cost 500 tokens. Message 30 costs 15,000+, because it's re-reading everything before it. One developer tracked a 100+ message chat: 98.5% of all tokens were spent re-reading old history. Only **1.5% went toward new output**.

On top of your messages, Claude also re-loads your `CLAUDE.md` file, all connected MCP server tool definitions, system prompts, and referenced files on every single turn. This overhead is invisible but constant.

**Bloated context doesn't just cost more — it produces worse output.** Research on the "lost in the middle" phenomenon shows models pay less attention to content buried in long contexts. Keeping context tight isn't just a cost move. It's a quality move.

---

## Tier 1 Hacks

### 1. Start Fresh Conversations

Use `/clear` between unrelated tasks. Don't carry context about topic A) into topic B). Evert message in a long chat is exponentially more expensive than the same message ni a fresh chat. This single habit is the #1 thing that extends session life.

### 2. Disconect MCP Servers

Every connected MCP server loads **ALL** its tool definitions into your context on **EVERY** message, even if you never touch it. One server alone = ~17,600 tokens per message. Run `/mcp` at the start of each session. Disconnect everything you won't use. Use CLIs instead.

### 3. Batch Prompt Into 1 Message

Three separate messages cost 3x what one combined message costs. Instead of **"summarize this"** → **"now extract the issues"** → **"now suggest a fix"**, send it all in one prompt. If Claude gets something slightly wrong, **edit your original message and regenerate** instead of sending a follow-up correction. Edits replace the bad exchange entirely.

### 4. Plan Mode Before Any Real Task

Claude maps out its approach and you approve before it writes a single line. Prevents the single biggest source of token waste: Claude going down the wrong path, writing code, then needing to undo and redo.

Add this to your `CLAUDE.md`:

> "Do not make any changes until you have 95% confidence in what you need to build. Ask me follow-up questions until you reach that confidence."

### 5. Run `/context` and `/cost`

- `/context` shows you exactly what's eating your tokens right now: conversation history size, MCP overhead, loaded files, everything.
- `/cost` shows your actual token usage and estimated spend for the current session. Most people have no idea where their tokens are going.

**These two commands make the invisible visible. You can't fix what you can't see.**

### 6.

### 7.

### 8.

### 9.

---
