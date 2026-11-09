---
name: shared-agents-md
description: >-
  Gives a whole team one set of agent instructions on Leverage: a workspace
  AGENTS.md that every agent session reads, in every repo and every harness.
  Use when the user says "share our CLAUDE.md with the team", "keep AGENTS.md
  in sync across the team", "same agent instructions for everyone", or
  "team-wide conventions for agents". Not for writing a CLAUDE.md for this one
  repo.
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Shared AGENTS.md for the team

On Leverage, the workspace and each space have an `AGENTS.md` in Git that
every session there reads, whether Claude Code, Codex or Grok Build runs it,
and in every repo. Owners and admins publish changes directly, other
members' changes go to review, and nobody copies files between laptops
again. A repo's own AGENTS.md or CLAUDE.md still applies inside that repo.

A committed AGENTS.md works for one repo; rules that span repos get copied
again.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=shared-agents-md` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: `leverage sessions new "Team AGENTS.md" --space <space> --file ./CLAUDE.md --prompt "Merge the attached instructions into the workspace AGENTS.md and publish."`.
