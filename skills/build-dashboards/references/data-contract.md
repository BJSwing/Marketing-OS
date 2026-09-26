# Dashboard data contract

Each project has two published pages, each with its own live database (the page's `db` store). Agents write to these stores with the artifact database tool (`ArtifactData`, also called `read_db` / `write_db`), passing the page's `url`. The pages read them live.

The project's markdown files stay the master copy. The stores are a live mirror of them, plus the owner's taps on the control panel, which the next agent step copies back into the markdown files (see "Owner actions" below).

All times are ISO 8601 with a time zone (`2026-09-26T14:05:00-04:00`). Never write a value you don't have: leave the field out, and the page shows an empty state. Never write sample or placeholder data.

## Control panel store

| Document | Fields | Written when |
| --- | --- | --- |
| `project/meta` | `name`, `slug`, `owner`, `approver`, `filesLink`, `mapUrl`, `updatedAt` | Build; any change to `system/project.md` |
| `project/rules` | `approval` (object: `routine_social_post`, `automated_email_flow`, `email_to_full_list`, `blog_or_page_change`, `dm_reply`, `ad_change`, each `ask_me` / `auto_ship`), `killSwitch` (`on` / `off`), `killSwitchAt`, `daily_cap`, `weekly_cap` (numbers, left out when `OPEN`), `currency`, `spend_under_cap`, `updatedAt` | Build; any change to `brand/approval-rules.md` or `brand/budget-rules.md` |
| `approvals/<id>` | `type` (`social_post`, `email`, `email_full_list`, `page_change`, `dm_reply`, `ad_change`, `spend`), `title`, `channel`, `body`, `incoming` (DM only), `amount` (spend only), `score`, `why`, `requestedBy`, `when` (planned send time, plain words), `previewUrl`, `previewAlt`, `sourceFile`, `status` (`pending`, `approved`, `rejected`, `handled`, `published`), `created`, `decidedAt`, `decidedBy`, `decisionNote`, `synced` | Every item queued; every status change |
| `activity/<id>` | `at`, `agent`, `action`, `item`, `result` (use `published`, `sent`, `posted` or `shipped` for anything that went public, so "Who shipped it" counts it) | Every line added to `system/activity-log.md` |
| `agents/<key>` | `state` (`running`, `idle`, `waiting`, `paused`), `status` (one short line), `perms`, `updatedAt` | When an agent starts, finishes, waits on approval, or is paused |
| `metrics/week` | `weekOf`, `shipped`, `shippedPrev`, `spend`, `kpis` (up to 3: `label`, `value`, `unit`, `prev`, `source`), `series` (`label`, `points`: `[{d, v}]`, oldest first, up to 12), `updatedAt` | The weekly Analytics report |
| `requests/<id>` | Written by the page, never by agents: `kind` (`decision`, `kill_switch`, `pause_agent`, `resume_agent`), `target`, `decision`, `value`, `note`, `at`, `by`, `applied` | The owner taps a button |

Agent keys: `watcher`, `orchestrator`, `research`, `content`, `creative`, `publisher`, `email`, `analytics`, `community`.

Approval ids: `<YYYY-MM-DD>-<short-name>`, the same name as the markdown file in `approvals/`.

Activity ids: `<YYYYMMDD-HHMMSS>-<agent>`. A store holds at most 5,000 documents, so keep the newest 300 `activity` documents and delete older ones when adding. The markdown log keeps everything.

`metrics/week` numbers come only from a real report. `shipped` counts items with a public result in the activity log for the week. `spend` is the sum of approved spend that actually landed this week, by the date it landed. KPIs come from `analytics/kpi-model.md`; a KPI whose target or source is `OPEN` is left out.

## Map store

| Document | Fields | Written when |
| --- | --- | --- |
| `project/meta` | `name`, `slug`, `owner`, `panelUrl`, `updatedAt` | Build; project changes |
| `project/summary` | `openQuestions` (count of unchecked lines in `system/open-questions.md`), `updatedAt` | Any time an OPEN is answered or added |
| `tools/<job-key>` | `job`, `tool`, `connected` (true/false), `status` (`picked` / `gap`), `pickedOn`, `why` | Every row added or changed in `system/tools.md` |
| `files/<folder>-<file>` | `folder`, `file`, `open` (number of `OPEN` in that file) | Build; any brand file edited |
| `phases/p1` … `p6` | `status` (`not_started`, `in_progress`, `done`), `doneOn`, `note` | When a build-order phase starts or its "done when" is met |

File keys drop `.md`: `brand/voice-guide.md` → `brand-voice-guide`.

Build-order phases: p1 Foundation, p2 See the market, p3 One working department, p4 Ship it, p5 Measure and react, p6 Close the loop. Mark a phase `done` only when its "Done when" line on the map is true, and ask the owner if unsure.

### Job keys

The map matches each job by key. Use the key in the left column; the middle column is the job name in the tool library.

| Key | Tool library job | Map part |
| --- | --- | --- |
| `search-queries` | Search queries | Signals |
| `site-behavior` | Site behavior | Signals |
| `competitor-ranks` | Competitor ranks | Signals |
| `search-interest` | Search interest | Signals |
| `social-insights` | Social insights | Signals |
| `audience-intel` | Audience intel | Signals |
| `channel-analytics` | Channel analytics | Signals |
| `mentions` | Mentions | Signals |
| `crm-contacts` | CRM and contacts | System of record |
| `content-calendar` | Content calendar | System of record |
| `asset-drive` | Asset drive | System of record |
| `playbook-wiki` | Playbook wiki | System of record |
| `customer-data-platform` | Customer data platform | System of record |
| `store` | Store | System of record |
| `audience-list` | Email and SMS list | System of record |
| `reasoning` | Reasoning | Brain |
| `agent-runner` | Agent runner | Brain |
| `memory-store` | Memory store | Brain |
| `visuals` | Images | Brain |
| `voiceover` | Voiceover | Brain |
| `live-research` | Live research | Brain |
| `research-intel` | Research and intel | Departments |
| `content-engine` | Content drafting and editing | Departments |
| `creative-studio` | Creative | Departments |
| `distribution-publishing` | Scheduling and publishing | Departments |
| `audience-email` | Email, newsletters, landing pages | Departments |
| `analytics-optimization` | Analytics | Departments |
| `social-posts` | Social posts | Engage |
| `email-out` | Email out | Engage |
| `cross-post` | Cross-post | Engage |
| `dm-replies` | DM and comment replies | Engage |
| `pipelines-etl` | Pipelines | Data |
| `transform` | Transform | Data |
| `warehouse` | Warehouse | Data |
| `reporting` | Reporting | Data |
| `error-tracking` | Error tracking | Data |

A job with no document shows "Not researched yet". A job the owner skipped is written with `status: gap`.

## Owner actions (control panel → markdown)

The owner can do four things on the control panel: approve or send back an item, pause or resume one agent, and flip the kill switch. Each tap updates the store at once and adds a `requests` document with `applied: false`.

Before any marketing work, the `project-rules` skill:

1. Lists `requests` where `applied` is `false`, oldest first.
2. Applies each one to the markdown files:
   - `decision`: set `status` in `approvals/<target>.md` and add the owner's note. Then set `synced: true` on `approvals/<target>`.
   - `kill_switch`: set `kill_switch` in `brand/approval-rules.md` and add a change-log row (`Who`: owner, via control panel). Then set `killSwitchSynced: true` on `project/rules`.
   - `pause_agent` / `resume_agent`: add or remove the agent under `paused_agents:` in `brand/approval-rules.md`, with a change-log row.
3. Sets `applied: true` and `appliedAt` on the request, and logs the change to the activity log.

Safety rule: if `project/rules.killSwitch` in the store is `on`, treat the kill switch as on even before it is copied into the markdown file. A paused agent in `agents/<key>` is paused the same way.

The control panel never changes approval rules or spend caps. Those change only in chat, as `project-rules` describes.
