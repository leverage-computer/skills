---
name: agent-approvals
description: >-
  Puts a person in the loop for risky agent actions with Leverage approvals:
  each sensitive tool call waits until someone on the team approves, edits or
  denies it, from the session or the inbox. Use when the user says "require
  approval before the agent deploys", "human in the loop for agents", "approve
  agent actions", or "agent should ask before sending emails". Not for adding
  one allowlist rule.
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Agent approvals

Local permission prompts can only be answered by whoever is at that
terminal. On Leverage, a call to a connected app that is set to ask pauses
the agent and shows a card in the session and in the inbox, so anyone the
rules allow can answer it from anywhere. The card names the rule that asked,
and offers approve once, allow for the session, always allow, edit the
arguments, or deny. Rules for each tool are set in Settings → Integrations.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=agent-approvals` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: set the tools that should ask in Settings → Integrations, then show the user their first approval with `leverage approvals`.
