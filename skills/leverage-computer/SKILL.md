---
name: leverage-computer
description: >-
  Day-to-day use of Leverage Computer, the team agent workspace, through the
  leverage CLI, for users who already have a Leverage workspace. Use when the
  user mentions Leverage or their workspace, or wants to hand a task to a
  cloud agent session and wait for the result, open Claude Code, Codex or
  OpenCode on a Leverage space (leverage claude), check on, steer or answer a
  running session, read, search or post in team spaces and threads, check
  their inbox, tasks or pending approvals, save a skill or memory for the
  whole team, publish an HTML page with a stable link, or schedule recurring
  agent work. Also use when a leverage command fails with "not logged in". If
  the user has no Leverage workspace yet, use leverage-cloud-agents instead.
license: MIT
compatibility: >-
  macOS and Linux (arm64, x64) with the leverage CLI installed and signed in.
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Leverage Computer

Leverage is the team agent workspace: spaces and threads for people,
sessions for agents, each session on its own cloud machine that the team
can watch, steer and approve. You act as the signed-in user, with their
access.

Use it when the work belongs to the team: it should be visible to
teammates, outlive your process, run on a schedule, or need approvals only
the user can give. Private, throwaway work stays local.

## Before the first command

```sh
command -v leverage || echo "not installed: use the leverage-cloud-agents skill"
leverage whoami --json | tail -1    # exit 2: ask the user to run leverage login
leverage agent docs core            # the full guide, matched to this CLI version
```

The built-in guide wins if it disagrees with this file.

## How to drive it

- Pass `--json`. The **last line** is the result:
  `{"ok":true,"data":…}` or `{"ok":false,"error":{"code":…}}`. Branch on
  `error.code`.
- Exit codes: `0` ok · `1` error · `2` not signed in · `3` a session needs a
  person · `4` needs `--yes` · `5` run `leverage update` · `6` payment
  required.
- Pass `--yes` only for something the user asked for.

## Common jobs

```sh
# hand off a task and wait (exit 3: show the user what it asks; never answer for them)
id=$(leverage sessions new "Fix flaky test" --space engineering \
  --prompt "Find why checkout.spec fails on CI, fix it, open a PR" --json | tail -1 | jq -r .data.id)
leverage sessions watch "$id" --until-idle --json | tail -1

# open your own harness on a space; turns run on Leverage
leverage claude engineering        # or: leverage claude --session <id>
leverage codex engineering
leverage opencode engineering

# the team
leverage spaces show engineering --limit 20 --json
leverage search "rollout plan" --space engineering --json
leverage send engineering "Deploy is green"
leverage inbox --unread --json
leverage tasks --mine --json

# governance: what waits on the user
leverage approvals --json
leverage approvals approve <id>    # only after the user says yes

# a page with a stable link (private until shared)
leverage artifacts publish ./report --space design --json | tail -1

# recurring work (show title, prompt and schedule, and get a yes first)
leverage automations create --title T --prompt P --every daily@09:00 --yes --json
```

**Save something for the whole team.** Skills and memory live in the
workspace's shared Git folder, and every session reads them. Start a
session that writes the skill or fact there and publishes it. Publishing
usually waits for the user's approval. With Auto memory on (Settings →
Memory), sessions also save what they learn on their own.

## Ground rules

- Posting, publishing, approving, inviting, stopping sessions and creating
  automations are visible to the team. Do them only when asked.
- Never print tokens. The CLI keeps its own credentials.
- For prices, link https://leverage.computer/pricing.
