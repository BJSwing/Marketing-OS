---
name: research-tools
description: Researches and recommends the right tool for each marketing module of a Marketing OS project, starting from the shared tool library and checking the web for options that fit this project better. Use during onboarding stage 7, or when the user asks "research tools for [module]", "which tool should we use for scheduling / email / analytics", "find a better tool for", or "re-check our tools".
---

# Research tools for a project

Each module picks its own tools based on what this project needs. The shared library in `references/tool-library.md` is the starting point, never the final answer.

## Before starting

1. Confirm the active project: read its `system/project.md`. If no project is active or it's unclear which one, ask. Never research for one project using another project's files.
2. Read what the project needs: `distribution/channel-playbooks.md`, `research/audience-icp.md`, `brand/budget-rules.md`, `system/tools.md` (tools already picked) and `research/source-list.md` (tools already in use).
3. Note which connectors are available in this session. A connected tool is a strong point in its favor.

## For each module

Work one module at a time. For each job in the module:

1. **Start from the library.** List the library's options for this job. Treat any entry whose version date is more than 90 days old as unconfirmed: check the vendor's current plan before recommending it.
2. **Search for a better fit.** Use web search for tools suited to this project's channels, industry, size, region or budget that the library doesn't list. Open the vendor pages you rely on; a search snippet is not a source.
3. **Compare 2 to 4 options** in a short table: tool, what it costs (from the vendor page, with the date checked), how well it fits this project, whether a Claude connector exists. Recommend one and say why in one sentence.
4. **The owner decides.** Ask them to pick one or skip. Never pick for them.
5. **Record it.** Add a row to `system/tools.md` with the job, tool, whether it's connected, today's date and the reason. A skipped job goes in as `GAP`, never a guess. If the project has a Project Map, update its `tools/<job-key>` document too (keys are in the `build-dashboards` skill's data contract).
6. **Suggest additions to the library.** If research found a tool the library lacks and it was the better fit, add a row to `system/tool-suggestions.md` with the date, job, tool, free or paid, why it was better here and the source link.

## Rules

- **Never edit `references/tool-library.md`.** Projects can't change the shared library. The owner reviews each project's `tool-suggestions.md` and adds approved tools in the next plugin version.
- **Money.** Never sign up for, start a trial of, or buy a tool. Recommend only.
- **Logins.** Never write passwords, API keys or account details in any file.
- **Pricing.** State prices only from a vendor page opened in this session, with the date. If you couldn't check, say "price not confirmed".

## Done when

Every job in the module has a picked tool or a `GAP` in `system/tools.md`, and the owner has seen each comparison.
