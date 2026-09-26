# Design documents

These are private to BJ unless shared from each page's Share menu.

| Document | What it shows | Link |
| --- | --- | --- |
| Marketing OS Blueprint | Layers, flow of information, the nine agents and their permissions, the event loop, build order | https://claude.ai/artifact/H646Nzou5r1JMLFRKVXLTQ |
| Control Panel design | Phone and desktop screens for the owner's dashboard | https://claude.ai/artifact/8Jex7yKaw87PgyQd3VnXJE |
| Onboarding spec | The nine onboarding stages, files, tool research and rules | https://claude.ai/code/artifact/8dd0a9ed-05b3-4cc3-b204-94ae797d736f |

## Digital Marketing Pro test (2026-09-25, v3.31.1)

- No background hooks; posting and sending need an explicit confirm step.
- Banned-word check worked. Voice scores separated on- and off-brand posts only narrowly (78 vs 63).
- Fact check caught an unsourced statistic and a "best" claim but missed a placeholder link. Marketing OS runs its own checks as well.
- Approval queue stores one file per item. Spend is text only, not enforced; Marketing OS enforces caps itself.
