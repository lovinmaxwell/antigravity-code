# Antigravity Code

A Cursor plugin for driving Google Antigravity CLI (`agy`) from Cursor or Grok Bot agents: install and auth, headless `-p` runs, model selection, and conversation continue/resume.

## Prerequisites

- Antigravity CLI (`agy`) installed.
- A Google / Gemini account (interactive `agy` login), or CI-style `GEMINI_API_KEY` with `modelProvider: "gemini"` in Antigravity CLI settings.
- Official docs: <https://antigravity.google/docs/cli/headless/>.

## Install for local testing

1. Copy this directory to:

   ```text
   ~/.cursor/plugins/local/antigravity-code
   ```

2. Reload Cursor with **Developer: Reload Window**.
3. Confirm the skills appear in Customize settings.

## Use from chat

Ask Cursor or Grok Bot to run Antigravity in a named repository, for example:

> Run Antigravity headless in `/path/to/repo` with model `gemini-3.5-flash-medium` to summarize the failing tests.

The skills cover setup/auth, local interactive guidance, headless `-p` with `--model` / `--effort` / `--continue`, and permission warnings for `--dangerously-skip-permissions`.

## Publishing

Cursor marketplace: <https://cursor.com/marketplace/publish>.
