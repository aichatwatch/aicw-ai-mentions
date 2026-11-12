---
title: Agent skill
description: Install the optional skill that teaches an AI agent to use the MCP tools.
---

The MCP server gives an agent the tools. The skill gives the agent a workflow. The package ships the skill in `skills/aicw-ai-mentions/SKILL.md`. Use it with agents that support `SKILL.md` files, such as Claude Code and Codex.

The skill tells the agent to:

- list saved scans and read one scan before it starts a new one;
- check for an OpenRouter key before a scan;
- store a key only when you give one on purpose;
- pass `templateText` when you want custom questions;
- rebuild a report from saved data instead of running a new scan;
- never invent a key and never print a key back to you;
- prefer local stdio MCP over an exposed HTTP server.

Install the MCP server first. See [MCP server](/mcp-server).

## Install from a source checkout

Run these three commands from the root of the repository. The first creates the skill folders. The other two copy the skill to Claude Code and Codex.

```sh
mkdir -p ~/.claude/skills "${CODEX_HOME:-$HOME/.codex}/skills"
```

```sh
cp -R skills/aicw-ai-mentions ~/.claude/skills/
```

```sh
cp -R skills/aicw-ai-mentions "${CODEX_HOME:-$HOME/.codex}/skills/"
```

## Install from a global npm install

First, find the skill folder in the global package.

```sh
SKILL_SRC="$(npm root -g)/aicw-ai-mentions/skills/aicw-ai-mentions"
```

Then create the folders and copy the skill. Run these in the same shell, so that `SKILL_SRC` is still set.

```sh
mkdir -p ~/.claude/skills "${CODEX_HOME:-$HOME/.codex}/skills"
```

```sh
cp -R "$SKILL_SRC" ~/.claude/skills/
```

```sh
cp -R "$SKILL_SRC" "${CODEX_HOME:-$HOME/.codex}/skills/"
```
