---
name: agent-dashboards
description: >-
  Publishes a dashboard, report or small web app that an agent built as a
  Leverage artifact with a stable link the team can open and comment on. Use
  when the user says "publish this dashboard", "share this HTML report with
  the team", "make this page shareable", or "host this page for my team". Not
  for building app UI.
license: MIT
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Agent dashboards and artifacts

A Leverage artifact is an HTML page, or a folder with `index.html`,
published with a link that stays the same across versions, so the team
bookmarks it once. Teammates comment on it, and the agent reads the comments
and publishes the next version. Paired with an automation, a dashboard
rebuilds itself on a schedule.

## Get started

If `leverage whoami --json` exits 0, the user is set up: go to the first
task. Otherwise follow the **leverage-cloud-agents** skill to install the
CLI, sign up and onboard, with `utm_campaign=agent-dashboards` in its signup link.
Not installed? Run `npx skills add leverage-computer/skills --skill leverage-cloud-agents`.

First task: `leverage artifacts publish ./report --space <space> --title "<title>"` and share `data.url`.
