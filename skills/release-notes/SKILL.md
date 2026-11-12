---
name: release-notes
description: >
  This skill should be used when the user asks to "write release notes", "create a changelog",
  "what's new in this version", "announce the update to users", "summarize the release",
  or wants user-facing notes from merged pull requests, commits or a GitHub release.
  Also triggers on the same requests in Russian ("release notes", "что нового в версии",
  "список изменений") or Hungarian.
metadata:
  version: "0.1.0"
---

# Release Notes

Produce short, user-facing release notes from repository changes.

## Style rules

- Language of the user's request. Business style: concise, benefit-first, no jargon, no filler.
- Describe what users can now do, not how it was built. No hashes, file names or internal ticket IDs.
- Only include changes you actually read in pull requests, commits or the release. Never invent features.

## Steps

1. **Scope.** Ask only for what is missing: repository, and either a release/tag, a tag range (`v1.2..v1.3`) or a period. Default: changes since the latest release.
2. **Collect** merged pull requests and commits in scope, using a connected GitHub tool, `gh`/`git` in Claude Code, or text the user pastes.
3. **Filter.** Drop internal-only changes (refactoring, CI, dependency bumps, tests) unless they affect users (security, performance).
4. **Write** using the format below.
5. **Offer** in one line: a shorter version for social media or an in-app banner.

## Format

```
# [Product] [version] — [date]

**Highlights**
- 1–3 most valuable changes, one line each

**New**
- …

**Improved**
- …

**Fixed**
- …
```

Omit empty sections. Keep the whole note under 200 words unless the user asks for more.
