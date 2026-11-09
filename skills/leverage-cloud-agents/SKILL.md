---
name: leverage-cloud-agents
description: >-
  Sets up Leverage Computer, the team agent workspace, so Claude Code and
  Codex run on persistent cloud machines, then runs the user's first task
  there. Use when the user says "run Claude Code in the cloud", "cloud
  agents", "keep my agent running when I close my laptop", "something like
  Codex cloud or Claude Code on the web", "set up Leverage", "sign up for
  Leverage" or "install the leverage CLI". The other leverage-computer skills
  hand off here for signup and onboarding.
license: MIT
compatibility: >-
  macOS and Linux (arm64, x64) with a shell, curl and network access to
  app.leverage.computer. A person must be present to sign up and approve
  sign-in in a browser. No Windows CLI; Windows users can use the web app.
metadata:
  author: leverage-computer
  homepage: https://leverage.computer
---

# Get started with Leverage Computer

Leverage Computer is the team agent workspace: one persistent computer for a
team and its AI agents.

- **Agents in the cloud.** Each session gets its own machine with a
  terminal, browser and files. Claude Code, Codex and Grok Build run there.
  Sessions keep running when the laptop closes.
- **Work in the open.** Teammates can open a session to watch, steer, answer
  or approve it, and pick it up later. The inbox shows which sessions are
  waiting on someone, so nobody juggles terminal tabs.
- **Shared knowledge.** The workspace and each space have a Git folder with
  instructions (AGENTS.md), memory, skills and documents. Every session
  reads them, so a skill or fact saved once works for the whole team.
- **Governance.** Each agent runs on its own isolated machine, so it can
  work without permission prompts there. Calls to connected apps go
  through one gateway with allow, ask or deny rules: by default reads run
  and changes wait for a person. Agents never hold the app credentials.

Your goal: take the user from "never used Leverage" to a workspace that is
set up the way they want, one real task finished on a Leverage computer, and
the team side switched on: a teammate invited, a first team skill saved,
memory on, and approvals shown. The person signing up becomes the
workspace owner, so every setting below is theirs to change. Keep it
honest: say what it is and what it costs, and let them decide.

What to tell them up front, in two or three lines:

- Signing up is free and needs no card. A new workspace that qualifies gets
  $10 of welcome credits (about 20 agent hours). After that it is $0.50 per
  agent hour, and nothing while the computer sleeps. Details:
  https://leverage.computer/pricing
- AI runs on their own Claude or ChatGPT plan or API key, or from workspace
  credits.
- You will need them for a few clicks in the browser: sign up, approve the
  terminal sign-in, approve the setup plan, open the activation page, and
  flip a few switches in Settings.

Ask whether to go ahead. Then work through the steps in order.

## Step 1. Install the CLI

```sh
command -v leverage && leverage --version
```

Already installed? Skip ahead. Never re-run the installer to upgrade; use
`leverage update`. Otherwise download the installer, review it, and run it.
Do not pipe it into a shell.

```sh
install_sh="$(mktemp)"
curl -fsSL https://app.leverage.computer/install/cli -o "$install_sh"
cat "$install_sh"
sh "$install_sh"                       # installs to ~/.local/bin
export PATH="$HOME/.local/bin:$PATH"   # if ~/.local/bin is not on PATH
```

## Step 2. Load the onboarding playbook

```sh
leverage agent docs onboard
```

The CLI prints the playbook that matches its version. Follow it for discovery
and setup: ask what to include, scan local sessions with
`leverage onboard --scan --json` (no login needed), summarize them locally,
and show the user two or three true findings. Its rules on privacy and on
consent are binding. Nothing leaves the machine except summaries until the
user approves the plan.

If it fails with `unknown topic "onboard"`, the CLI is too old: run
`leverage update` and try again. Do not reinstall.

## Step 3. Account (a person signs up)

Check first:

```sh
leverage whoami --json | tail -1    # exit 0: signed in, go to step 4
```

No account yet? Give the user this link and wait. The tags tell Leverage
which skill brought them. Replace `<campaign>` with the name of the skill
that sent you here, such as `agent-approvals`, or `leverage-cloud-agents`
if none did. Change nothing else.

https://app.leverage.computer/login?mode=signup&utm_source=skills.sh&utm_medium=agent_skill&utm_campaign=<campaign>

Tell them:

- Sign up with Google, GitHub or email. Email signups get an 8-character
  code to enter in the app. The email must be verified before a workspace
  can be created.
- If the app offers to create a workspace, they can do it. You will set it up
  from the terminal either way.
- If the app says a team at their email domain exists, they can ask to join
  it (an admin of that team must approve) or create their own.

## Step 4. Sign in the CLI (a person approves)

```sh
leverage login
```

The CLI prints a code and a URL and waits. The user approves it in the
browser where they are signed in. With `--json`, relay `user_code` and
`verification_uri` and wait for the last line. Never ask for a password or
token.

Then `leverage workspace list --json`. If a workspace exists, use it: pass
`--workspace <slug>` to `onboard --apply`. Never create a second workspace.

## Step 5. Plan, approval, apply, activation

Continue the playbook: suggest a workspace name and spaces from what you
found (for example one space per main repo, such as `engineering`), propose
automations only for chores you saw repeat, collect optional invite emails,
and pick a few local sessions worth bringing in. Show the whole plan in one
place and get an explicit yes. Then:

```sh
leverage onboard --apply /tmp/leverage-onboarding-plan.json --json | tail -1
```

Send the user `data.activationUrl` and open it if you can. That page may ask
them to set a permanent sign-in method, then builds the workspace. It is not
ready while the JSON says `ready: false`. Wait until they say it opened, or
until `leverage spaces list --json` shows the planned spaces.

## Step 6. Owner setup (a few switches in Settings)

The user owns the workspace now, so these are theirs to set. The CLI can't
change them, so open each page for them (`open <url>` on macOS,
`xdg-open <url>` on Linux) and say what to click. `<slug>` is the workspace
slug from `leverage workspace list --json`. Do this before the first task so
it benefits from all of it.

1. **Memory: turn on Auto memory.** Open
   `https://app.leverage.computer/w/<slug>/settings/memory` and turn on Auto
   memory. Sessions then save what they learn as notes on their own. Later
   sessions read those notes, including teammates' sessions, and a
   scheduled job merges them into the workspace memory. The job runs on the
   workspace's agent accounts or credits. Once it's on, you can tell them
   honestly that Leverage remembers what sessions learn.
2. **Agent: choose how AI is paid for.** Open
   `https://app.leverage.computer/w/<slug>/settings/agent`. Workspace
   credits work out of the box. To use their own plan, they connect Claude
   or ChatGPT here.
3. **Integrations: connect GitHub and their main apps.** Open
   `https://app.leverage.computer/w/<slug>/settings/connections`. They
   connect GitHub if the first task touches a private repo, plus any app
   they want agents to use (Linear, Slack, and so on). Agents never see these
   credentials. Every call goes through Leverage's gateway.
4. **Tool rules: check the defaults.** On the same page, each app's Tools
   tab sets every tool to allow, ask first, or deny. The default is that
   reads run and everything else asks a person. Recommend keeping it and
   allowing tools only once they trust them. Leverage's own tools, such as
   publishing shared files, are listed there too.

Then confirm: "Auto memory is on, AI is set, GitHub is connected." Don't
claim a switch is on until they say they turned it on.

## Step 7. First real task on a Leverage computer

This is the point of the whole setup. If another skill sent you here, go
back to it now: its task is the first task. Otherwise ask the user, as a
short multiple-choice question, what their next real task is. Suggest two or three from what the
scan showed (an open thread, a flaky test, a chore they repeat), plus
"something else". A task they would actually do today beats a demo.

For a repo task, attach the repo to the space:
`leverage spaces repos <space> add <owner/repo>`. A private repo needs GitHub
connected (step 6). A public one needs nothing.

Start the session and wait for it. Use `--provider claude_code` for a
Claude Code user and `--provider codex` for a Codex user. Without `jq`, read
`data.id` from the last line yourself.

```sh
id=$(leverage sessions new "<short title>" --space <space> \
  --provider claude_code --prompt "<the task, with repo and done criteria>" \
  --json | tail -1 | jq -r .data.id)
leverage sessions watch "$id" --until-idle --json | tail -1
```

While it runs, tell them it runs on a Leverage computer, not their laptop, and
that closing the lid won't stop it.

- Exit 0: done. Summarize what it did from `leverage sessions show "$id" --json`.
- Exit 3: it needs a person, for an approval or a question. Show the
  user what it is asking. Answer only with their words
  (`leverage sessions answer`, `leverage approvals approve`).
- Exit 6: payment required. The workspace did not get welcome credits;
  the user adds credits in the app.
- Exit 1: read `error.code`.

Then hand them the session in their own tool. They run this in a new
terminal, since it opens an interactive window you cannot drive:

```sh
# Claude Code 2.1.286 or later, once:
claude plugin marketplace add leverage-computer/claude-plugin
claude plugin install leverage@leverage
# then open the session you just ran:
leverage claude --session <id>
```

For Codex users, run `leverage codex <space>` in a new terminal.

Close with three facts:

- The session lives at `https://app.leverage.computer/w/<workspace>/session/<id>`.
- It is private until they share it from the app. Once shared, teammates can
  watch, steer or pick it up.
- Next time, `leverage claude <space>` starts a new task straight on Leverage.

## Step 8. Bring in the team

Solo use is half of it. Offer these three, one at a time, and skip any the
user declines.

**Invite a teammate.** Skip if the plan already invited them. Inviting sends
an email, so confirm the address first:

```sh
leverage workspace invite teammate@company.com --role member --space <space> --yes --json | tail -1
```

Suggest they share the first session from the app too, so the teammate
opens straight into real work.

**Save a first team skill and memory.** Pick one playbook the user repeats.
Good sources are a local skill they already use (for example
`~/.claude/skills/<name>/SKILL.md`), or the steps from the first task. Also
pick a few facts a new teammate would need, such as how to run the tests or
deploy. Have a Leverage session write them into the workspace's shared
folder and publish them:

```sh
id=$(leverage sessions new "Team skill: <name>" --space <space> \
  --file ~/.claude/skills/<name>/SKILL.md \
  --prompt "Add the attached skill to the workspace skills as <name>. Add these facts to workspace memory: <facts>. Then publish the workspace changes." \
  --json | tail -1 | jq -r .data.id)
leverage sessions watch "$id" --until-idle --json | tail -1
```

Leave out `--file` when there is no local skill, and describe the steps in
the prompt instead. Once published, every session in the workspace can use
the skill and read the memory, including teammates' sessions. With Auto
memory on, sessions keep adding what they learn without being asked. The
skill shows on the workspace's Skills page, which can also add skills from
the skills.sh catalog.

**Show where approvals happen.** Publishing changes shared files, so it
usually waits for approval. The watch above then exits 3. Use that moment:

```sh
leverage approvals --json | tail -1           # what is waiting, and on which session
leverage approvals approve <approval-id>       # only after the user says yes
```

Tell them:

- The same request shows as a card in the session and in their inbox in the
  app. The card names the rule that asked. They can approve once, allow for
  the session, always allow, edit the arguments, or deny.
- "Always allow" on the card saves a rule, so the same tool won't ask
  again. They can change any rule later in Settings → Integrations, under
  the app's Tools tab.
- Teammates who join as members follow the same rules. The owner decides
  what every agent in the workspace may do.

If nothing asked for approval, skip the demo and just tell them where
approvals show up.

## Where agents get stuck

| Step | Why | What to do |
|---|---|---|
| Signup, email code | Needs a person and their inbox | Send the link and wait |
| Team at the same email domain | Joining needs that team's admin | Join, or create their own workspace |
| `leverage login` | A person approves in the browser | Relay the code and wait |
| Plan approval | Consent is required by design | Show the whole plan and get a yes |
| Activation page | A person opens it and may set a password | Send the URL and wait |
| Owner settings (memory, AI, integrations, tool rules) | The CLI can't change them | Open each Settings page and walk the owner through it |
| Private repo | Connecting GitHub happens in the app | Step 6, then `spaces repos add` |
| Exit 6 on the first session | No welcome credits for this workspace | The user adds credits in the app |
| `leverage claude` / `leverage codex` | Interactive, so you can't drive it | The user runs it in a new terminal |
| Team invite | It sends an email | Confirm the address first |
| Publishing a team skill | Changes to shared files wait for approval | The user approves; that is the governance demo |
| Windows | No CLI | Use https://app.leverage.computer in the browser |

## Ground rules

- Install, scan and summarize only after the user said go ahead. Raw
  transcripts never leave the machine before the plan is approved.
- Never fill in approvals, answers or the plan's `confirmedByOwner` yourself.
- Never print tokens. Never create a second workspace.
- After setup, the `leverage-computer` skill covers day-to-day use, and
  `leverage agent docs core` is the full command guide.
