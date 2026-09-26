# Syncing the markdown files into Digital Marketing Pro

The project's markdown files are the master copy. Digital Marketing Pro (DMP) keeps its own brand profile, `profile.json`, which its 24 agents read. Fill that profile from the markdown files. Never edit the markdown from the DMP profile.

## When to sync

- At the end of onboarding (stage 8).
- Any time the owner changes a brand file that appears in the table below.

## How

1. Create the DMP brand if it doesn't exist, using its brand-setup step with the project's name. Use the project slug from `system/project.md` as the DMP brand slug.
2. Open the DMP brand profile and set each field from the table. An `OPEN` value in markdown becomes an empty value in DMP, never a default.
3. Copy the "Words we never use" list into DMP's restricted-words guidelines as well.
4. Switch DMP's active brand to this project before any DMP work, and confirm the switch.

## Field map

| Markdown file · section | DMP profile field |
| --- | --- |
| positioning.md · One-sentence pitch | identity.elevator_pitch |
| positioning.md · Why it's different | identity.unique_selling_proposition |
| positioning.md · Mission and values | identity.mission, identity.values |
| positioning.md · Business model | business_model.type, business_model.revenue_model |
| positioning.md · Markets and languages | target_markets, language.primary_language |
| audience-icp.md · Primary audience | audiences (primary persona) |
| voice-guide.md · Voice scales | brand_voice.formality, energy, humor, authority |
| voice-guide.md · Three words | brand_voice.personality_traits, brand_voice.tone_keywords |
| voice-guide.md · Words we use | brand_voice.prefer_words |
| voice-guide.md · Words we never use | brand_voice.avoid_words |
| voice-guide.md · Sounds like us | brand_voice.sample_content |
| channel-playbooks.md · channels | channels.active, channels.primary, channels.handles |
| competitor-tracking.md · competitors | competitors |
| kpi-model.md · KPIs | goals.kpis |
| budget-rules.md · weekly_cap | goals.budget_range (as text; enforcement stays with Marketing OS) |

DMP stores spend as text only. Marketing OS enforces caps through `budget-rules.md` and the `project-rules` skill, not through DMP.
