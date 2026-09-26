---
name: build-dashboards
description: Builds a Marketing OS project's two live dashboards - the Control Panel (approvals, spend, agents, kill switch, activity) and the Project Map (the blueprint showing this project's tools, open questions and build progress) - publishes them as private pages, and fills them from the project's files. Use at the end of onboarding, or when the user says "build the dashboards", "build the control panel", "make the project map", "rebuild the dashboards", "refresh the dashboards", or "sync the dashboards".
---

# Build a project's dashboards

Every Marketing OS project gets the same two pages, built from the templates in this skill:

| Page | Template | What it shows |
| --- | --- | --- |
| **Control Panel** | `templates/control-panel.html` | Phone-first. Home (items waiting, shipped, KPIs, spend vs cap, trend, who shipped), Approvals (approve or send back each item), Agents & rules (pause agents, approval bar, caps, kill switch), Activity. On a desktop all four show side by side. |
| **Project Map** | `templates/project-map.html` | The Marketing OS blueprint (Blueprint, Flow, Agents, The Loop, Build Order), with this project's picked tool on every job, gaps marked, open questions per brand file, and build-order progress. |

Both pages read live data from their own database. Agents keep that data current; the pages update on their own. The exact documents and fields are in `references/data-contract.md`. Read it before writing any data.

## Rules

- **Only this project.** Read `system/project.md` first. Never put another project's data in these pages.
- **No made-up numbers.** Write only values that come from the project's files or a real report. Anything unknown is left out, and the page shows an empty state. Never seed sample data.
- **Markdown stays the master copy.** The page databases mirror the files. Owner taps on the Control Panel flow back into the files through the `project-rules` skill.
- **No passwords, keys or logins** in a page or its database.
- **Pages are private.** They're published to the owner's account. Don't share them; the owner decides.

## Step 1 · Check what exists

Read `system/project.md`. If it already has `control_panel_url` and `map_url`, this is a refresh: skip to step 4. If only one exists, build only the missing one.

If the Artifact tool or the artifact database tool is not available in this session, say which one is missing and stop. Don't build a substitute.

## Step 2 · Make the two pages

For each template:

1. Copy it to a working file named `<slug>-control-panel.html` or `<slug>-map.html`.
2. Replace every `{{PROJECT_NAME}}` with the project name. Change nothing else.
3. Publish it with the Artifact tool as a new artifact:
   - `file_path`: the working file
   - `icon`: `dashboard` for the Control Panel, `map` for the Project Map
   - `description`: "Live control panel for <Project Name>" or "Live project map for <Project Name>"
   - Control Panel `capabilities`: `{"db": {"rules": [{"path": "", "read": "interact", "write": "admin"}]}, "user": {}}`
   - Project Map `capabilities`: `{"db": {"rules": [{"path": "", "read": "interact", "write": "admin"}]}}`

   The rule means only people who can edit the page (the owner) can approve, pause or change anything. Viewers can only look.
4. Keep the returned URL.

## Step 3 · Record the links

Add both URLs to the `dashboards` block in `system/project.md` (`control_panel_url`, `map_url`), save the file to the project's location, and add a line to `system/activity-log.md`.

## Step 4 · Fill the data

Use one batched write per page wherever possible.

**Control Panel store**, from the files:
- `project/meta` from `system/project.md`, with `mapUrl`
- `project/rules` from `brand/approval-rules.md` and `brand/budget-rules.md` (numbers as numbers; leave out any cap that is `OPEN`)
- One `approvals/<id>` per file in `approvals/` (status as in the file)
- `activity/<id>` for the newest 300 lines of `system/activity-log.md`
- `agents/<key>` only for agents that have actually run; leave the rest out
- `metrics/week` only if a weekly report exists

**Project Map store**, from the files:
- `project/meta` with `panelUrl`
- `project/summary` with the count of unchecked lines in `system/open-questions.md`
- One `tools/<job-key>` per row in `system/tools.md` (the key table is in the data contract)
- One `files/<folder>-<file>` per brand file, with its count of `OPEN`
- `phases/p1` … `p6` from the onboarding log and what exists; ask the owner if a phase's status is unclear

On a refresh, first apply any unapplied owner requests (as `project-rules` describes), then rewrite every document from the files so the pages match them.

## Step 5 · Check it

1. List each collection you wrote and confirm the counts match the files.
2. Read `project/rules` back and confirm the kill switch and caps match the markdown.
3. Open each page once with the Artifact tool's open action so the owner sees it.

## Finish

Tell the owner in two lines: the Control Panel and the Project Map are live, and what they'll see first (for example: "1 item waiting, 7 open questions, 9 of 36 jobs filled"). The page cards carry the links.

## Keeping them live

After the build, every agent step keeps the pages current, as set out in the data contract and the `project-rules` skill:
- A new approval item, a decision, or a published item → update `approvals/<id>` and add an `activity` line.
- A tool picked or skipped → update `tools/<job-key>` on the map.
- An OPEN answered → update `files/…` and `project/summary` on the map.
- The weekly Analytics report → update `metrics/week`.

If the owner says "sync the dashboards", run step 4 again.

## Updating the design

The templates belong to the plugin. Projects never edit them. To change the design for every project, edit the templates here, bump the plugin version, and run "rebuild the dashboards" in each project: publish the new template to the existing URL (pass `url`) without `capabilities`, so the page keeps its database and data.
