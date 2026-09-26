# Onboarding stages in detail

Follow each stage in order. End every stage by appending `| <stage> | <YYYY-MM-DD> | <one-line note> |` to `system/onboarding-log.md`.

## Stage 1 · Start

Ask, one at a time:

1. What is the project or brand name?
2. Who owns it, and who approves posts and spend? (Often the same person.)
3. Are we in a claude.ai Project that belongs only to this brand? If no, stop and ask the owner to create one, then resume there.
4. Where should this project's files live? Offer two choices:
   - **Google Drive** — a folder named `Marketing OS – <Project Name>`. Use the Google Drive connector. If it isn't connected, say so and offer to connect it.
   - **GitHub** — a repository the owner names. The repo must hold only this project. If the owner has none, ask them to create an empty one and share the link.
   If neither tool is available in this session, say which connection is missing and wait.

Build the project slug: lowercase, spaces and symbols to single hyphens, at most 60 characters.

Copy the template tree into a working folder. Fill `system/project.md`. Record the plugin version from the plugin manifest.

## Stage 2 · Import

Ask where existing material lives. Accept any mix of: website link, social handles, a Drive folder, uploaded files (brand guide, decks, past emails), an existing marketing context file from another plugin, or "nothing yet".

For each source:
- Read it. For a website, fetch the home, about and main product pages.
- Record it in `research/source-list.md` with what it was used for.
- Pull out facts only when the source states them directly. Note the source next to each fact you'll use later.

Show the owner a short list of what was found and ask them to confirm or remove anything outdated. Do not use a fact the owner removed.

If Digital Marketing Pro is installed and the owner has a brand guide document, also run its `import-guidelines` step on that document.

## Stage 3 · Interview

Use Digital Marketing Pro's full 17-question setup as the question list (brand identity, business model, audience, voice and messaging, marketing context). If DMP is not installed, use the same topics:

1. Brand name
2. One-sentence pitch
3. What makes it different
4. Mission and values
5. B2B, B2C or both
6. Industry and category
7. How it makes money
8. How long a typical sale takes
9. Primary customer: who they are, what they need
10. Secondary customer, if any
11. What makes them buy, and what stops them
12. Three words for the voice
13. Three to five core messages
14. Words and claims to avoid
15. Active channels and the goal for each
16. Three to five competitors
17. Markets and languages

Pre-fill every answer that stage 2 found, citing the source, and ask the owner to confirm with a yes or a correction. Ask only the questions still blank. If the owner skips one, write `OPEN`.

Write answers to `brand/positioning.md`, `research/audience-icp.md`, `research/competitor-tracking.md`, `distribution/channel-playbooks.md` and `analytics/kpi-model.md`.

## Stage 4 · Voice

Ask for:
- Three real pieces that sound right (posts, emails, page copy). Links or pasted text.
- Three that sound wrong: a competitor, an old post, or anything the owner dislikes.
- Words the brand uses often, and words it never uses.

Map the three voice words to 1–10 scores for formality, energy, humor and authority. Show the scores and ask the owner to adjust them. Write `brand/voice-guide.md`, `brand/tone-rules.md` and `brand/messaging-bank.md`. A proof point goes in the messaging bank only with its source.

## Stage 5 · Approval bar

Show the rules in `brand/approval-rules.md`, all set to `ask_me`. Explain in one line that the owner can loosen any rule later.

Ask, one at a time and only if the owner wants to change something now: should any of these ship without asking? Routine social posts, automated email flows, email to the full list, blog or page changes, DM replies, ad changes. Record each change in the file's change log with the date.

## Stage 6 · Spend

Ask:
1. Daily spend cap, and currency.
2. Weekly spend cap.
3. Should spend under the cap still ask you, or go through? (`ask_me` or `auto_ok`.)

Keep `agents_can_spend_alone: false` whatever the answers. If the owner doesn't know a cap yet, leave it `OPEN`; with any cap `OPEN`, every spend request asks.

## Stage 7 · Tools

Load the `research-tools` skill and run it for each module in this order: Signals, System of record, Creative, Distribution and publishing, Email, Analytics, Engage. The Brain and Data layers usually need no per-project pick; ask the owner whether to skip them.

## Stage 8 · Write and connect

1. Make sure every template file exists, with answers filled in and `OPEN` everywhere else.
2. Rebuild `system/open-questions.md`: one checkbox per `OPEN`, naming the file and the question to ask.
3. Create an `approvals/` folder in the project.
4. Save everything to the location chosen in stage 1:
   - Google Drive: create the folder tree and files with the Drive connector.
   - GitHub: clone the repo, add the files, commit with the message `Marketing OS onboarding: <Project Name>`, and push. Ask before pushing if the repo is not empty.
5. If Digital Marketing Pro is installed: sync the brand into it as described in `dmp-sync.md`, then run DMP's `cowork-setup` so its data persists through Google Drive.

Tell the owner the link to the saved folder.

## Stage 9 · Test post

1. Pick the owner's primary channel from `distribution/channel-playbooks.md`.
2. Draft one post using only the project files. Do not use anything from the conversation that isn't in the files. This proves the files carry the brand.
3. Run every check in `test-post-checks.md`.
4. If a check fails, name the file behind the failure, ask the one question that fixes that file, update it, and redraft. Repeat until every check passes.
5. Put the post in the approval queue: DMP's approval manager if installed (type `schedule-social`, risk `low`), otherwise a markdown file in `approvals/` named `<date>-test-post.md` with status `pending`.
6. Ask the owner to approve or reject it. Record the answer. Do not publish it either way.

## Stage 10 · Dashboards

Load the `build-dashboards` skill and follow it. It publishes this project's Control Panel and Project Map, records both links in `system/project.md`, and fills them from the files written in stage 8, including the test post from stage 9.

If the Artifact tool isn't available in this session, say so, mark stage 10 unfinished in the log, and finish the summary. The owner can say "build the dashboards" later from a session that has it.
