---
name: antigravity-local
description: Guide interactive Google Antigravity CLI (agy) use in a working directory. Use when the user wants an interactive agy session, model listing, agents listing, or local Antigravity IDE/CLI guidance (not a one-shot headless -p run).
---

# Antigravity local

Use this skill when the user wants interactive Antigravity on this machine rather than a one-shot headless `-p` run.

## Working directory

Prefer the repository or path named by the user as the working directory.

## Interactive session

Start interactive Antigravity:

```bash
agy
```

List models and agents the user can choose:

```bash
agy models
agy agents
```

Pin a model or agent for an interactive session when the user names one (exact slug from `agy models` / `agy agents`). Never invent model slugs.

## Permissions

Prefer scoped allow rules in `~/.gemini/antigravity-cli/settings.json` over blanket approval. Only mention `--dangerously-skip-permissions` when the user explicitly wants unattended full auto-approve, and warn that it approves all tool calls including shell and file writes.

For scripted one-shot tasks, use the headless skill instead.
