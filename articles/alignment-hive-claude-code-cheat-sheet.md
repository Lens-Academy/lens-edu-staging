---
title: "Claude Code Cheat Sheet"
author:
  - "Alignment-hive"
source_url: "https://www.alignment-hive.com/cheatsheet"
published: 2026-10-08
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "Essential commands, shortcuts & files"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Essential commands, shortcuts & files

## Keyboard Shortcuts ^keyboard-shortcuts

| Shortcut | Action |
| --- | --- |
| `Esc` | Interrupt generation |
| `Shift+Tab` | Cycle modes |
| `Ctrl+R` | Search history |
| `Esc Esc` | Rewind message |
| `Shift+Enter` | Newline |
| `Ctrl+B` | Background task |
| `↑ / ↓` | Prompt history |
| `Ctrl+C` | Cancel / force stop |
| `Ctrl+G` | Edit in $EDITOR |

## Input Syntax ^input-syntax

| Syntax | Action |
| --- | --- |
| `@path/file` | Attach file to prompt |
| `!command` | Run bash directly |
| `/command` | Slash command or skill |

## CLI ^cli

| Command | Action |
| --- | --- |
| `claude` | Interactive session |
| `claude -c` | Continue last session |
| `claude -r` | Resume any session |
| `claude -p "…"` | Non-interactive mode |
| `claude --chrome` | Enable chrome |
| `claude --dangerously-skip-permissions` | Bypass all permissions |

## Commands ^commands

| Command | Action |
| --- | --- |
| `/help` | List all commands |
| `/clear` | Clear conversation |
| `/compact` | Compress context window |
| `/resume` | Resume another session |
| `/copy` | Copy last message |
| `/rewind` | Rewind to earlier message |
| `/config` | Open configuration |

## Permission Modes ^permission-modes

| Mode | Behavior |
| --- | --- |
| **Normal** | Manually approve file edits |
| **Accept Edits** | Auto-allow file edits |
| **Plan** | Planning only |
| **Bypass** | Fully autonomous |

## Key Files ^key-files

| File | Purpose |
| --- | --- |
| `CLAUDE.md` | Project memory — read every session |
| `.claude/settings.json` | Project settings (shared with team) |
| `CLAUDE.local.md` | Personal project memory (gitignored) |
| `.claude/settings.local.json` | Personal project settings (gitignored) |
| `~/.claude/CLAUDE.md` | Global memory — all projects |
| `~/.claude/settings.json` | Global settings — all projects |

[code.claude.com/docs](https://code.claude.com/docs) · Press `?` in session for current shortcuts
