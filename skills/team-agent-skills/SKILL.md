---
name: team-agent-skills
description: >-
  Rolls agent skills out to a whole team on Leverage, so every session has
  them and one update reaches everyone. Use when the user says "share skills
  with my team", "install this skill for everyone", "team skill library", or
  "everyone's agent should follow this playbook". Not for writing a new skill
  from scratch.
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Team skills

On Leverage, a skill's folder decides who gets it: workspace skills reach
every session, space skills reach one space, and personal skills reach one
person. One update reaches everyone, and a skill can be turned off without
deleting it. The workspace's Skills page adds skills straight from the
skills.sh catalog.

Skills committed to one repo don't follow people into other repos, and
global installs drift.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=team-agent-skills` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: `leverage sessions new "Team skill: <name>" --space <space> --file ~/.claude/skills/<name>/SKILL.md --prompt "Add the attached skill to the workspace skills as <name> and publish."`. Publishing usually waits for the owner's approval.
