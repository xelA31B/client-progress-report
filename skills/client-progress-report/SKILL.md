---
name: client-progress-report
description: >
  This skill should be used when the user asks for a "weekly report for the client",
  "progress report from GitHub", "what did the team ship this week", "status update for the
  stakeholder", "summarize the repo activity", "client update", "what was done on the project",
  or wants a plain-language summary of development work (commits, pull requests, issues,
  releases) for a non-technical client, owner or manager. Also triggers on the same requests in
  Russian ("отчёт для заказчика", "что сделали за неделю", "статус проекта") or Hungarian.
metadata:
  version: "0.1.0"
---

# Client Progress Report

Turn repository activity into a short, professional status report that a non-technical client can read in two minutes.

## Style rules

- Write in the language of the user's request. Keep repository, branch and product names as-is.
- Business style: concise, factual, no filler, no narration. Bullets and tables over paragraphs.
- Translate technical work into outcomes the client cares about: features, fixes, risks, dates. No commit hashes, file names or jargon in the main report.
- Never invent progress. Every item must trace back to a commit, pull request, issue or release you actually read. If data is missing, say so.
- Do not judge individual developers. Report on the work, not on people.

## Step 1 — Inputs

Ask in one short message only for what is missing:

1. Repository (owner/repo or URL); several repositories are allowed.
2. Period — default: last 7 days.
3. Audience — **Client** (non-technical, default) or **Team lead** (adds technical appendix).
4. Detail level — **Detailed** (default), **Standard**, or **Brief** (5 bullets for a chat message or email).
5. Optional: project milestones or deadlines to report against.

## Step 2 — Collect activity

Use whichever source is available, in this order:

1. A connected GitHub tool (GitHub connector / MCP).
2. In Claude Code: `gh` CLI or `git log` in the local repository.
3. If neither is available, ask the user to connect GitHub in Claude settings, or to paste the list of merged pull requests / commits for the period.

Collect for the period:

- Merged pull requests (title, description, labels, linked issues)
- Commits on the default branch not covered by a merged PR
- Issues opened and closed; open issues labelled bug, blocker or high priority
- Releases and tags
- Open pull requests older than 5 days or with failing checks
- CI status of the default branch, if available

## Step 3 — Analyse

Group the work into client-facing categories:

- **Delivered** — features and improvements now available
- **Fixed** — bugs resolved
- **In progress** — open pull requests and active issues
- **Risks / blockers** — stalled PRs, failing builds, critical open bugs, missed milestones
- **Next** — what logically follows (open PRs close to merge, planned issues)

Also group every item by **area** (e.g. Website/UI, Mobile, API/integrations, Search & social visibility, Security, Performance, Payments, Content, Infrastructure) and record its **date**.

Detail rules:

- **Detailed (default):** one line per meaningful change — do not merge distinct changes. Each line: what changed → what it means for the client/users, with the date. Add the activity metrics table, the day-by-day timeline and evidence for every risk (e.g. "menu fixed 4 times on 11 Nov").
- **Standard:** merge closely related changes into one line per area; keep metrics, drop the timeline.
- **Brief:** status + 5 bullets, no tables.

Skip pure maintenance (dependency bumps, formatting, typos) unless it matters to the client; count it in one line ("+12 maintenance updates").

When the repository has no plan for next week (no open milestones, issues or PRs), say so in one line and suggest 2–3 next steps that follow logically from the open risks and unfinished work, clearly marked as suggestions.

## Step 4 — Write the report

Use `references/report-template.md` for the chosen detail level. Detailed: up to two pages. Standard: one page. Brief: one screen. Add the technical appendix only for the Team lead audience or on request.

Close with one line offering: release notes for end users (`release-notes`), or a report for another period.

## Deliverable

Deliver as a document artifact if available, otherwise formatted markdown in chat, plus a short summary in the chat reply.

## Branded report

If the environment can render HTML artifacts or files, deliver the full report using `references/report-template.html` (fill the placeholders, keep the design and colours; use the score ring for the main score and status chips for pass / warn / fail / not checked). Otherwise use the markdown format above. Keep the chat reply to a short summary either way.

## Recurring run

At the end of the report, offer a recurring run. Recommended cadence: weekly, on Friday afternoon, for the past 7 days (or at the end of each sprint).

Let the user choose their own schedule. Ask in one short message, with the recommendation pre-filled:

- **Frequency:** daily · weekly · every 2 weeks · monthly · quarterly · custom
- **Day:** e.g. Monday, Friday, 1st of the month
- **Time and time zone:** e.g. 09:00 Europe/Budapest (use the user's time zone if known)
- **Delivery:** in this chat, a new chat, or a document

If the environment offers scheduled tasks (a scheduling tool is available), create the task only after the user confirms these choices. Write the scheduled prompt so it is self-contained: what to check (project, repository or company), which skill to run, the report language, and where to deliver the result. Confirm what was scheduled in one line. The user can change or cancel the schedule at any time; when asked, update or remove it.

If no scheduling tool is available, state the chosen or recommended cadence and suggest a calendar reminder.
