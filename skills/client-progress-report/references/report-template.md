# Report template

Write in the language of the request; translate headings. One line per item.

## Client version (one screen)

```
# Project update — [Project] · [period]

**Status:** 🟢 On track / 🟡 Attention needed / 🔴 Blocked — one-line reason

## Delivered
- Outcome in plain words (what the client can now do / see)

## Fixed
- Problem that no longer happens

## In progress
- Item — expected next step

## Risks & decisions needed
- Risk or blocker — what is needed and from whom
(write "None" if empty)

## Next week
- 2–4 bullets

_Basis: N merged changes, N issues closed, N releases · source: [repo]_
```

Status rule: 🔴 if a blocker or failing main build exists; 🟡 if a milestone is at risk, critical bugs are open or PRs are stalled; otherwise 🟢.

## Team lead appendix (on request)

```
## Technical appendix
| Area | Item | PR / issue | State |
|------|------|------------|-------|

- Stalled PRs (> 5 days): …
- CI on default branch: passing / failing since …
- Open critical issues: …
```
