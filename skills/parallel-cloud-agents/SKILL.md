---
name: parallel-cloud-agents
description: >-
  Runs several coding agents at once, each on its own Leverage cloud machine
  with its own checkout, and tracks them to the finish. Use when the user says
  "run 5 agents in parallel", "parallel agents", "multiple Claude Code
  sessions at once", or "try three approaches at the same time". Not for
  subagents inside this session or creating a single worktree.
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Parallel agents

Running several agents on one laptop means juggling worktrees, ports, memory
and battery, and checking each tab to see which one needs you. On Leverage,
every session gets its own cloud machine and checkout, so agents can't
collide. One inbox shows which ones are waiting on the user.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=parallel-cloud-agents` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: one `leverage sessions new "<approach>" --space <space> --prompt "<task>"` per task, then `leverage inbox --unread`.
