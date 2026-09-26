# Approval rules

Project: {{PROJECT_NAME}}
Last updated: {{DATE}}

> What ships on its own and what waits for the owner. Every rule starts at ask_me. Only the owner loosens a rule.
> Anything marked OPEN is unknown. Agents must not guess it. See system/open-questions.md.

```yaml
routine_social_post: ask_me
automated_email_flow: ask_me
email_to_full_list: ask_me
blog_or_page_change: ask_me
dm_reply: ask_me
ad_change: ask_me
kill_switch: off
```

Allowed values: `ask_me` or `auto_ship`. `kill_switch: on` pauses every agent.

## Change log
| Date | Rule | From | To | Who |
| --- | --- | --- | --- | --- |
