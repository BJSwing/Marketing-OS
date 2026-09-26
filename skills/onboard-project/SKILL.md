---
name: onboard-project
description: Sets up Marketing OS for a new brand or client in one guided session - imports existing brand material, interviews the owner only for what is missing, sets approval and spend rules, researches tools per module, writes the project's brand files, and runs a test post into the approval queue. Use when the user says "onboard a new brand", "set up Marketing OS for [brand]", "start a new marketing project", "new client setup", "resume onboarding", or "/onboard-project".
---

# Onboard a project

Turn one brand into a running Marketing OS project. Work through ten stages in order. Each stage is detailed in `references/stages.md`; read it before starting stage 1 and follow it exactly.

## Non-negotiable rules

1. **Never fill a blank with a guess.** If the owner has not said it and no imported source states it, write `OPEN` and add a line to `system/open-questions.md`. Do not use Digital Marketing Pro's quick-setup defaults.
2. **Ask, don't infer.** When an imported source and an answer disagree, show both and ask which is right.
3. **One question at a time, phone-friendly.** Short questions. Offer multiple choice (AskUserQuestion) where the answer is a choice. Accept short answers.
4. **Start strict.** Every approval rule starts at `ask_me`. `agents_can_spend_alone` is always `false`. Only the owner loosens a rule, and only by saying so.
5. **Nothing goes public during onboarding.** The test post goes to the approval queue only.
6. **No passwords, API keys or logins in any file.** Record which tool is used, never how to log in.
7. **One project only.** Read and write only inside this project's folder. Never open another project's files. If the current claude.ai Project already holds a different brand, stop and ask the owner to open a Project for this brand.
8. **Markdown files are the master copy.** The project's `/brand` … `/system` files are the source of truth. Digital Marketing Pro's profile is filled from them (see `references/dmp-sync.md`), never the other way round.
9. **Resumable.** After each stage, add a line to `system/onboarding-log.md` with the date. On "resume onboarding", read the log and continue at the first unfinished stage.

## Before stage 1

- Check whether Digital Marketing Pro is available (its skills or commands appear as `digital-marketing-pro:*`). If it is not, tell the owner in one line that onboarding will still work but the 24 DMP agents won't be connected until it's installed, and continue.
- If `system/onboarding-log.md` already exists for this project, this is a resume. Say which stage is next and continue there.

## The ten stages

| Stage | Goal | Writes |
| --- | --- | --- |
| 1 Start | Name, owner, approver, where files live | `system/project.md`, `system/onboarding-log.md` |
| 2 Import | Find and read what already exists | `research/source-list.md` |
| 3 Interview | Fill brand facts; ask only what's missing | `brand/positioning.md`, `research/audience-icp.md`, `research/competitor-tracking.md`, `distribution/channel-playbooks.md`, `analytics/kpi-model.md` |
| 4 Voice | Real examples, words to use and ban | `brand/voice-guide.md`, `brand/tone-rules.md`, `brand/messaging-bank.md` |
| 5 Approval bar | Confirm what asks and what may auto-ship | `brand/approval-rules.md` |
| 6 Spend | Caps and whether spend under cap still asks | `brand/budget-rules.md` |
| 7 Tools | Each module researches its tools | `system/tools.md`, `system/tool-suggestions.md` |
| 8 Write and connect | Write all files; sync DMP; save to the chosen location | Whole project folder |
| 9 Test post | Draft from the files alone, check, queue it | First item in the approval queue |
| 10 Dashboards | Build the live Control Panel and Project Map | Two private pages, links in `system/project.md` |

Stage 7 uses the `research-tools` skill in this plugin. Load it at stage 7. Stage 10 uses the `build-dashboards` skill. Load it at stage 10.

## Files

- Templates for every project file: `templates/` in this skill's folder. Copy the whole tree for a new project, replacing `{{PROJECT_NAME}}`, `{{PROJECT_SLUG}}`, `{{DATE}}` and the other `{{…}}` fields. Leave every `OPEN` in place until it is answered.
- Field mapping to Digital Marketing Pro: `references/dmp-sync.md`.
- Test post checks: `references/test-post-checks.md`.

## Finishing

When stage 10 is done, give the owner a short summary:

- Where the project files live (link)
- How many questions are still OPEN, with the top three
- The approval rules and caps as set
- Tools picked, and jobs left as gaps
- The test post's status in the queue
- That the Control Panel and Project Map are live (their cards carry the links)

Then offer one next step: answer the open questions.
