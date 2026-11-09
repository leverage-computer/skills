---
name: agent-audit-log
description: >-
  Answers "what did the agent do and who allowed it?" with Leverage's record
  of every agent tool call, the rule that decided it and the person who
  approved it. Use when the user says "audit log for agents", "who approved
  this agent action", "what did the agent do last night", or "trace agent tool
  calls".
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Agent audit log

Local transcripts live on one laptop, anyone can edit them, and they don't
say who approved a call. On Leverage, each tool call in a session shows how
it was decided: auto-approved by a named policy, approved by a named person,
or denied. Session transcripts stay in the workspace for the team, every
completed agent turn is committed to Git, and Settings → Usage shows spend
and agent time.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=agent-audit-log` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: `leverage sessions show <id>` and summarize the relevant tool calls.
