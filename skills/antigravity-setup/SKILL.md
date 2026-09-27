---
name: antigravity-setup
description: Install, authenticate, and verify Google Antigravity CLI (agy). Use when agy is missing, auth fails, or before first Antigravity use from an agent.
---

# Antigravity setup

Use this skill before the first Antigravity task, or whenever the CLI is missing or authentication fails.

## Check the installation

Run:

```bash
agy --version
which agy
```

If `agy` is not installed, point the user to the official Antigravity install path at <https://antigravity.google> and the CLI docs. Do not invent an install script URL. Ask before installing anything heavy.

## Authenticate

Headless mode uses cached credentials. Authenticate once with an interactive session:

```bash
agy
```

Complete browser or account sign-in when prompted, then exit.

For CI or non-interactive environments without a prior login, configure API-key auth:

- Set `modelProvider` to `"gemini"` in `~/.gemini/antigravity-cli/settings.json`.
- Export `GEMINI_API_KEY` in the environment.

An unauthenticated headless run exits with an authentication error rather than hanging. Do not print API keys.

## Verify

List models (also confirms the CLI responds):

```bash
agy models
```

If authentication is required and interactive, stop and ask the user to finish login before continuing.
