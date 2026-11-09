---
name: agent-handoff
description: >-
  Moves a live coding-agent session, with its history, from this laptop onto a
  Leverage cloud machine where it keeps going or a teammate picks it up. Use
  when the user says "continue this Claude Code session elsewhere", "move this
  session off my laptop", "let my teammate pick this up", or "hand off this
  session". Not for writing a handoff summary document.
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Agent session handoff

A local session lives in one terminal on one laptop: it stops when the
laptop does, and a teammate gets at best an exported copy. Leverage imports
the session with its full history onto a cloud machine. There it keeps
running, and once the user shares it, a teammate continues the same session,
not a copy.

Claude Code keeps sessions as `.jsonl` files under `~/.claude/projects/`.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=agent-handoff` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: `leverage sessions import <session.jsonl> --title "<title>" --repo <owner/repo>`, then share it from the app.
