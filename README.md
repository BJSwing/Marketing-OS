# Marketing OS

A one-person AI marketing team you can set up for any brand. This plugin is the engine: it holds the setup process, the rules and the templates. Each brand gets its own separate project, and nothing from one brand leaks into another.

## What it does

| Skill | What it's for | Say something like |
| --- | --- | --- |
| **Onboard a project** | Sets up a new brand in one guided session of about 45 minutes | "Onboard a new brand" · "Resume onboarding" |
| **Research tools** | Each marketing module finds the best tool for this brand, starting from a shared tool library | "Research tools for email" · "Find a better scheduling tool" |
| **Project rules** | Keeps work inside one brand and enforces its approval, spend and kill-switch rules | "Switch to Tackle Jacket" · "Pause everything" · "Let routine posts auto-ship" |

## How the pieces fit

```text
Marketing OS plugin (this repo)      shared, read-only engine
  ├─ onboarding, rules, templates
  └─ tool library (starting point for research)

Digital Marketing Pro plugin         the brain: 24 agents, 163 skills
                                     installed separately, updates on its own

One claude.ai Project per brand      sealed; its own files, memory and approvals
  ├─ Common Club
  ├─ Tackle Jacket
  └─ any outside client
```

Each brand's files live where you choose at onboarding: a Google Drive folder or its own GitHub repo. The markdown brand files are always the master copy.

## Setting it up

You do these steps once. After that, every new brand is just step 3.

**1. Install Marketing OS on your account** so it's available in every project, in the Claude app and on your Mac.

- In the Claude app: open the `marketing-os.plugin` file from the chat where it was built and press the button to add it.
- Or in Claude Code: type these two lines, one at a time, pressing Enter after each.
  ```
  /plugin marketplace add BJSwing/Marketing-OS
  /plugin install marketing-os@bjswing-marketing-os
  ```

**2. Install Digital Marketing Pro** the same way. In Claude Code:
```
/plugin marketplace add indranilbanerjee/neels-plugins
/plugin install digital-marketing-pro@neels-plugins
```
Marketing OS still works without it, but the 24 agents won't be connected.

**3. For each brand:** create a new claude.ai Project named after the brand, open a chat in it, and say "onboard a new brand".

## The rules every project follows

- Nothing is guessed. Unknowns are marked `OPEN` and listed as questions.
- Every approval rule starts at "ask me". Only you loosen a rule.
- No agent can spend money on its own.
- Nothing goes public during onboarding.
- No passwords or keys are stored in any file.
- One project at a time; a project never reads another project's files unless you ask by name.

## Improving the engine

Projects never change this plugin. When a project's tool research finds something better, it writes it to that project's `system/tool-suggestions.md`. Review those, add the good ones to `skills/research-tools/references/tool-library.md` here, bump the version in `.claude-plugin/plugin.json`, and every project gets the update.

## Background

Designed in the "Agentic Marketing" claude.ai Project, September 2026: the blueprint, flow of information, agent roster, control panel design and onboarding spec. See `docs/links.md`.
