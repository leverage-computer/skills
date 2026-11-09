---
name: agent-inbox
description: >-
  Gives the user one Leverage inbox for everything their agents and their
  team's agents are waiting on: questions, approvals and finished work. Use
  when the user says "which agent needs me", "I keep losing track of my Claude
  tabs", "notify me when the agent is done", or "team inbox for agents".
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Agent inbox

Several agents in terminal tabs means checking every tab to see which one is
stuck. On Leverage, every session that needs a person lands in one inbox, in
the app and in the CLI: questions, tool approvals, finished work, across the
user's and the team's agents. Notifications are set in Settings →
Notifications.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=agent-inbox` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: `leverage inbox --unread` and `leverage approvals`, then answer only with the user's words.
