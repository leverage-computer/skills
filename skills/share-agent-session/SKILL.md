---
name: share-agent-session
description: >-
  Shares a live coding-agent session on Leverage so teammates can watch,
  steer, answer or take it over, and sets the team up to work with agents
  together in shared spaces. Use when the user says "share this Claude Code
  session", "let my teammate watch the agent", "pair on what the agent is
  doing", "multiplayer Claude Code", or "multiplayer agents". Not for
  exporting a transcript to a file for yourself.
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Share an agent session

A Leverage session lives in the workspace, not in one terminal, so sharing
it is a link. Teammates watch it live, queue or steer messages, answer its
questions and approve its tool calls, in the browser or in their own Claude
Code with `leverage claude --session <id>`. In a team space, anyone can
mention `@Leverage` in a thread to start a session the whole space can
follow.

Locally, `/export` gives a teammate a read-only copy, and live pairing means
a screen share or tmux over SSH.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=share-agent-session` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: share the session from the app, or start one in a space with `leverage send <space> "@Leverage <task>"`.
