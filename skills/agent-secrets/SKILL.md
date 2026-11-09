---
name: agent-secrets
description: >-
  Keeps API keys and credentials out of coding agents with Leverage: apps
  connect through its gateway, and secrets are added to HTTPS requests without
  ever entering the agent's machine. Use when the user says "keep API keys out
  of the agent", "the agent shouldn't see our secrets", "prompt injection
  could leak my keys", or "where do I put secrets for agents". Not for
  scanning code for hardcoded secrets.
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Keep secrets out of agents

If an agent can run commands on a machine that holds a key, it can read the
key and leak it. On Leverage, the key never enters the agent's machine.
Connected apps sign in once in Settings → Integrations and agents get only a
short-lived session token. Other API keys go in Settings → Variables and
secrets as "Added to requests": the machine holds a placeholder, and
Leverage adds the real header on HTTPS requests to the hosts you choose.

Claude Code deny rules such as `Read(./.env)` stop its file tools, but not a
shell command.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=agent-secrets` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: move the user's first key into Settings → Variables and secrets. Never ask them to paste it into chat.
