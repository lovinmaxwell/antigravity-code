---
name: antigravity-headless
description: Run Google Antigravity CLI headless with agy -p for scripted coding tasks. Use when the user wants non-interactive Antigravity, --model/--effort, continue/resume, json or stream-json output, or CI-style agy runs.
---

# Antigravity headless

Use this skill for non-interactive Antigravity CLI runs that print a result and exit.

## Prerequisites

Confirm `agy` is available and authenticated (setup skill). Prefer the user's named working directory.

## One-shot prompt

```bash
agy -p "prompt" --output-format json
```

Aliases for `-p` are `--print` and `--prompt`. Diagnostics go to stderr; the response (or JSON envelope) goes to stdout.

## Model and effort (prefer pinning when the user cares)

List slugs first if unsure:

```bash
agy models
```

Pin an exact slug the user named or that `agy models` returned. Do not invent slugs. Unknown `--model` values fail the run:

```bash
agy -p "prompt" --model gemini-3.5-flash-medium --output-format json
```

Optional reasoning effort:

```bash
agy -p "prompt" --effort high --output-format json
```

Optional agent:

```bash
agy agents
agy -p "prompt" --agent <agent-name> --output-format json
```

## Continue and resume

Continue the most recent conversation:

```bash
agy -p "follow-up" --continue --output-format json
```

Resume by conversation ID from a prior JSON result (`conversation_id`):

```bash
agy -p "follow-up" --conversation <conversation-id> --output-format json
```

Only use a conversation ID returned by the CLI or supplied by the user.

## Permissions

Workspace file read/write is typically allowed. Shell and other tools may soft-deny in headless mode unless allowed in settings. Prefer scoped `permissions.allow` rules. Use `--dangerously-skip-permissions` only when the user explicitly requests full auto-approve, and warn about the risk.

## Timeouts and output

Raise the wait ceiling for long jobs:

```bash
agy -p "prompt" --output-format json --print-timeout 15m
```

Parse JSON: report `status`, `response` or `error`, and `conversation_id` when useful. For live tool/progress monitoring, use `--output-format stream-json` and read the terminal `result` event.
