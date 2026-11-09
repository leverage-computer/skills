---
name: safe-yolo-mode
description: >-
  Lets coding agents run without permission prompts safely: on an isolated
  Leverage cloud machine where the agent runs freely, with approvals only for
  actions that reach real apps. Use when the user says
  "--dangerously-skip-permissions", "yolo mode", "too many permission
  prompts", or "skip permissions safely". Not for adding one rule to an
  allowlist.
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Safe yolo mode

Skipping permissions on a laptop hands the agent the user's home folder, SSH
keys, cloud credentials and every logged-in CLI. On Leverage, each session
runs on its own isolated cloud machine with permission prompts off, and that
machine holds no app credentials. Calls to GitHub, Slack, Stripe and other
connected apps go through Leverage's gateway, where reads run and anything
that changes things asks a person. So the agent never stops for `npm
install`, and still stops before it merges, deploys or sends.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=safe-yolo-mode` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: run the task the user wanted to run without prompts as a Leverage session.
