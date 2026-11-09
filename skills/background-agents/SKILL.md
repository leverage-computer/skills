---
name: background-agents
description: >-
  Hands a coding task to a background agent on a Leverage cloud machine so the
  user keeps working, then reports back. Use when the user says "send this to
  a background agent", "work on this in the background while I keep coding",
  "background agents like Cursor", or "fire and forget this task". Not for
  running a local command or subagent in the background.
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Background agents

A background agent run from the user's laptop competes for its CPU and
battery, and it dies when the lid closes. On Leverage, each task runs as a
session on its own cloud machine with its own checkout. It keeps going after
the laptop closes, and the user checks in from the CLI, the web app or their
own Claude Code.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=background-agents` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: `leverage sessions new "<title>" --space <space> --prompt "<task, finish line, what to do when stuck>"`.
