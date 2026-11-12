# Client Progress Report — Claude plugin

Turn GitHub activity into a status report your client reads in two minutes: what was delivered, what was fixed, what is in progress, what needs a decision.

## Install

**Claude app (web, desktop):** Plugins → add a marketplace from a GitHub repository → `xelA31B/client-progress-report` → install **Client Progress Report**. Once approved in the Claude directory, search for **Client Progress Report** in Plugins.

**Claude Code (VS Code or terminal):**

```
/plugin marketplace add xelA31B/client-progress-report
/plugin install client-progress-report@client-progress-report
```

## Skills

| Skill | What you get |
|-------|--------------|
| **client-progress-report** | One-screen weekly (or any period) update with status 🟢/🟡/🔴, delivered, fixed, in progress, risks, next steps. Optional technical appendix for team leads. |
| **release-notes** | Short user-facing release notes from merged pull requests, commits or a release. |

## Commands

Type `/` in Claude and pick a command:

| Command | What it does |
|---|---|
| `/changelog [owner/repo] [version or period]` | User-facing release notes from a repository |
| `/client-report [owner/repo] [period] [brief|standard|detailed]` | Client status report from GitHub activity |

## How to use

Ask Claude in any language:

- "Weekly client report for acme/webshop"
- "Сделай отчёт для заказчика по репозиторию acme/webshop за 2 недели"
- "Write release notes for v1.4 of acme/webshop"

## Requirements

GitHub access in Claude (the GitHub connector), `gh`/`git` in Claude Code, or a pasted list of pull requests / commits.

## Principles

- Concise, professional, no filler; always in the language of the request.
- Every line traces back to real repository activity. Nothing is invented.
- Reports on the work, never on individual developers.

## License

MIT
