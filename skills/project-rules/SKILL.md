---
name: project-rules
description: Keeps Marketing OS work inside one project and enforces that project's approval, spend and kill-switch rules. Use before any marketing work in a Marketing OS project (drafting, scheduling, sending, posting, spending), and when the user says "switch to [project]", "which project are we in", "pause everything", "kill switch", "turn the kill switch off", "change the approval rule for", "let [type] auto-ship", or "change the spend cap".
---

# Project rules

Every Marketing OS project is sealed. Apply these rules before and during any marketing work.

## 1. Know the active project

- Read `system/project.md` in the project folder. It names the project, its slug, owner, approver and where its files live.
- If no project is active, or the request could belong to more than one project, ask which one. Never guess.
- Switching projects happens only when the owner asks, by name. On a switch, say which project is now active. If Digital Marketing Pro is installed, switch its active brand to the same slug and confirm.

## 2. Stay inside it

- Read and write only inside the active project's folder.
- Never read another project's files unless the owner names that project and asks, for example "what worked for Tackle Jacket". Say out loud when you do.
- Start every file you create, log line and approval item with the project slug.
- Never copy brand details, contacts or results from one project into another.

## 3. Check the kill switch first

Read `kill_switch` in `brand/approval-rules.md`. If it is `on`, do no drafting for publication, scheduling, sending, posting or spending. Tell the owner the kill switch is on and stop.

## 4. Approvals

Before anything leaves the building (a post, an email, a reply, a page change, an ad change):

1. Find the matching rule in `brand/approval-rules.md`.
2. `ask_me` → put the item in the approval queue (Digital Marketing Pro's approval manager if installed, otherwise a file in `approvals/` with status `pending`) and stop. Do not publish.
3. `auto_ship` → allowed, but only after the content passes the checks in the onboarding skill's `references/test-post-checks.md`.
4. No matching rule → treat it as `ask_me`.

## 5. Money

- No agent spends alone. `agents_can_spend_alone` is always `false`, whatever else the file says.
- Every spend request goes to the approval queue with the amount, the reason and how it compares with the daily and weekly caps in `brand/budget-rules.md`.
- Flag any request that would pass a cap. If a cap is `OPEN`, every request asks.
- Keep spend dates exact: record the date a charge actually lands. Never present a yearly cost as a monthly saving.

## 6. Changing a rule

- Change an approval rule, cap or the kill switch only when the owner says so directly in this conversation.
- Repeat the change back before writing it. Record it in the file's change log with the date, old value, new value and who asked.
- Never loosen a rule on your own, even if it would be faster.

## 7. Log what happens

Append one line per action to `system/activity-log.md` (create it if missing): date and time, agent or skill, action, item, result. This is what the owner's control panel reads.
