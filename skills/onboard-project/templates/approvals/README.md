# Approval queue

Project: {{PROJECT_NAME}}

> One file per item waiting for the owner. Used when Digital Marketing Pro's approval manager isn't installed.

Each item file is named `<YYYY-MM-DD>-<short-name>.md` and starts with:

```yaml
project: {{PROJECT_SLUG}}
type: social_post | email | email_full_list | page_change | dm_reply | ad_change | spend
status: pending | approved | rejected | published
created: YYYY-MM-DD
requested_by: <agent or skill>
amount: <only for spend>
rule: <the approval rule that sent it here>
```

Then the content itself, and the check results.
