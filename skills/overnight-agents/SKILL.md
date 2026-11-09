---
name: overnight-agents
description: >-
  Runs a long coding-agent task overnight on a Leverage cloud machine so it is
  ready to review in the morning. Use when the user says "run this overnight",
  "work on it while I sleep", "long-running agent task", or "have it ready by
  morning".
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Overnight agents

Overnight runs fail when the laptop sleeps or when the agent stops at the
first permission prompt and waits until morning. A Leverage session runs on
its own cloud machine with permission prompts off, so the lid can close.
Only calls to connected apps that are set to ask wait for a person, and
those show up in the inbox.

Locally this means keeping the laptop open, awake and online all night.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=overnight-agents` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: `leverage sessions new "Overnight: <title>" --space <space> --prompt "<task>. Done when <finish line>. If blocked, write what you tried to NOTES.md and stop."`.
