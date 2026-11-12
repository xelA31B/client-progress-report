# Report templates

Write in the language of the request; translate headings. Business style, one line per item, no narrative paragraphs. Every item traces to real repository activity.

## Detailed (default, ≤ 2 pages)

```
# Project update — [Project] · [period]

**Status:** 🟢 On track / 🟡 Attention needed / 🔴 Blocked — one-line reason

## Summary
- 3–4 bullets: main result of the period, most important fix, main risk, decision needed

## Activity
| Metric | Value |
|--------|-------|
| Working days with changes | N (dates) |
| Changes merged | N |
| New features / improvements | N |
| Fixes | N |
| Issues closed / opened | N / N |
| Releases | N |

## Delivered — by area
### [Area, e.g. Website]
- [date] What changed → what it gives the client/users
### [Area, e.g. API]
- …

## Fixed — by area
### [Area]
- [date] Problem that no longer happens → impact (e.g. "launch blocker", "users affected")

## In progress
| Item | State | Expected next step |
|------|-------|--------------------|

## Risks & decisions needed
| Risk | Evidence | Impact | Recommended action | Owner |
|------|----------|--------|--------------------|-------|
(write "None" if empty)

## Timeline
| Date | Main work |
|------|-----------|

## Next steps
- From the repository: …
- Suggested (not in the repository): … — mark clearly as suggestions

_Basis: N merged changes, N commits, N issues, N releases · source: [repo] · period: …_
```

## Standard (1 page)

Same sections without Timeline; Delivered and Fixed merged to one line per area.

## Brief (one screen)

```
**[Project] · [period] · Status 🟢/🟡/🔴**
- Main result
- Key fix
- Key risk
- Decision needed
- Next step
```

Status rule: 🔴 if a blocker or failing main build exists; 🟡 if a milestone is at risk, critical bugs are open, PRs are stalled or there are no automated checks on direct pushes to production; otherwise 🟢.

## Team lead appendix (on request, any level)

```
## Technical appendix
| Area | Item | PR / commit | Date | State |
|------|------|-------------|------|-------|

- Stalled PRs (> 5 days): …
- CI on default branch: passing / failing / none
- Open critical issues: …
```
