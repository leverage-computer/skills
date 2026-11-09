---
name: scheduled-agents
description: >-
  Schedules recurring coding-agent work, such as a morning triage or a weekly
  report, as a Leverage automation that runs on a cloud machine even when
  every laptop is closed. Use when the user says "run this agent every
  morning", "cron job for Claude Code", "scheduled agents", or "recurring
  agent task". Only for jobs a coding agent does: not for ordinary cron jobs
  or CI workflows that run no agent.
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Scheduled agents

A cron job with `claude -p` needs a machine that's always awake, and a CI
run starts fresh each time with no one to approve anything. A Leverage
automation runs an agent session on a schedule, on a cloud machine, as the
user. It can keep one ongoing session so each run remembers the last. It can
pause for approvals, can be limited to its own tools, and posts its results
to a space.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=scheduled-agents` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: `leverage automations create --title "<title>" --prompt "<job>" --every weekdays@09:00 --space <space>`. Show the user the title, prompt and schedule and get a yes first.
