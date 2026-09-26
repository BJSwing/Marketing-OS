# Test post checks

Every check must pass before the test post goes to the approval queue. Run all of them even when Digital Marketing Pro's `check` step is available: in testing, DMP's fact check missed a placeholder link and rated a clearly off-brand post low-risk, so it is a second opinion, not the only one.

| Check | Pass when | File behind a failure |
| --- | --- | --- |
| Banned words | None of "Words we never use" appear, in any form (for example "curate", "curated") | voice-guide.md |
| Voice match | Reads like the "Sounds like us" examples and unlike the "Never sounds like us" examples; scores within 2 points of each voice scale | voice-guide.md |
| Claims | Every number, statistic or "best / #1 / leading" claim appears in messaging-bank.md with a source | messaging-bank.md |
| Links | No placeholder or made-up links (example.com, your-site.com, links not on the brand's real site) | positioning.md or channel-playbooks.md |
| Channel fit | Length, format and tags follow channel-playbooks.md and hashtag-rules.md | channel-playbooks.md |
| Tone rules | Follows tone-rules.md for this channel; avoids listed topics | tone-rules.md |
| Brand facts | Product names, prices and dates match positioning.md; nothing invented | positioning.md |

Report the result to the owner as a short table: check, pass or fail, and for a failure the one fix needed.
