---
name: team-agent-memory
description: >-
  Gives a team's coding agents shared memory on Leverage, so what one session
  learns, every later session knows, including teammates'. Use when the user
  says "team memory for agents", "my agent doesn't know what my teammate
  figured out", "agents forget everything between sessions", or "shared
  context across sessions".
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Team memory for agents

On Leverage, memory is Markdown in the workspace's Git folder, and every
session reads it before it starts. With Auto memory on (Settings → Memory),
sessions save what they learn as notes on their own, other sessions can read
them right away, and a scheduled job merges them into topics. Spaces have
their own memory, and personal memory stays private.

Claude Code's own auto memory is machine-local, so a teammate's agent never
sees it.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=team-agent-memory` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: have the owner turn on Auto memory, then seed it: `leverage sessions new "Seed team memory" --space <space> --prompt "Save these facts to workspace memory and publish: <facts>"`.
