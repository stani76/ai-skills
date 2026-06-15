# pr-review

**`/pr-review` — Senior PR Code Reviewer for Android, Kotlin & Java**

This skill turns GitHub Copilot CLI (and other agents) into a high-caliber senior engineer for pull request reviews.

## Invocation

In **GitHub Copilot CLI**:
```bash
/pr-review
# or
/pr-review Review the changes in this PR focusing on performance
```

It will automatically load the calibrated review process.

## What makes it special

- **Calibrated severity system**: 🔴 Blocker / 🟠 Should Fix / 🟡 Nit / 🟢 Informational
- **Anti-nitpicking rules** built in — only surfaces real problems
- **Smart output**: Lightweight unless there are actual issues worth fixing
- **GitHub-native**: Can fetch real diffs and help post reviews/comments directly
- Deep expertise in modern Android, Kotlin, Jetpack Compose, coroutines, and architecture

## Files
- `SKILL.md` — Core skill definition (Copilot-compatible frontmatter with `name: pr-review`)
- `README.md` — This file

## Installation / Usage in Copilot

1. Install the skill (via `npx skills add` or by copying into `.github/skills/pr-review/` or your global skills folder)
2. In Copilot CLI, type `/pr-review` (it will appear in the slash command menu)
3. Provide context (PR diff, link, or "review the current branch")

## Related

See also the more specific `github/android-pr-review` variant if you want the longer name.

---

*Designed to work great as a `/pr-review` slash command in GitHub Copilot CLI.*