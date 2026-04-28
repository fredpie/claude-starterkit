# Claude code Boilerplate

A ready-to-clone starting point for Claude Code as an agentic AI workspace. Ships with pre-configured plugins, skills, MCP server, hook, rules and workflow patterns so you can skip boilerplate and start building immediately.

Thi is a basic folder structure for `.claude` folder to include in your project.
It has the benefit to give a good structure to help you develop with you AI agents.

---

## Table of Contents

- [What This Is](#what-this-is)
- [How to Use This Boilerplate](#how-to-use-this-boilerplate)
- [Prerequisites](#prerequisites)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Configuration Files](#configuration-files)
- [Plugins](#plugins)
- [Skills (Slash Commands)](#skills-slash-commands)
- [MCP Servers](#mcp-servers)
- [Rules (Auto-Loaded Instructions)](#rules-auto-loaded-instructions)
- [Hooks & Scripts](#hooks--scripts)
- [Context Monitor Statusline](#context-monitor-statusline)
- [WAT Framework](#wat-framework)
- [Memory System](#memory-system)
- [Reference Docs](#reference-docs)

---

## What This Is

This framework wires together every layer of a Claude Code projects :

- **Rules :** Markdown instruction files auto-loaded into every session
- **Plugins :** Extend Claude Code with specialized modes (superpowers, frontend-design, agent-sdk, etc.)
- **Skills :** Reusable slash commands you invoke with `/skill-name`
- **MCP Servers :** 15 pre-configured Model Context Protocol integrations (Supabase, Google Workspace, Pinecone, Trigger.dev, n8n, Vapi, Apify, Alpaca, Monet, and more)
- **Hooks :** Lifecycle shell scripts that run on session start, stop and tool events
- **Scripts :** A context monitor statusline and a first-time setup bootstrapper
- **WAT Framework :** Architecture pattern : Workflow → Agents → Tools
