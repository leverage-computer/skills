---
name: agent-governance
description: >-
  Sets company-wide rules for what a team's coding agents may do with
  Leverage: allow, ask or deny per tool, roles, machine sizes and who pays for
  AI, enforced for every agent in the workspace. Use when the user says "agent
  governance", "control what our agents can access", "AI policy for our team's
  agents", or "lock down agent tools for the company".
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Agent governance

Per-laptop settings only cover one tool on one machine, and every machine
still holds its own credentials. On Leverage, the owner sets the rules once
and they apply to every agent in the workspace, whichever harness runs it.
Agents never hold app credentials, and each tool is set to allow, ask first
or deny. Workspace and space rules that ask or deny can't be loosened below
them, and roles (owner, admin, member, guest) control who changes them.

Claude Code's managed settings cover only Claude Code, and only on machines
IT manages.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=agent-governance` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: walk the owner through Settings → Integrations (tool rules) and Settings → Agent.
