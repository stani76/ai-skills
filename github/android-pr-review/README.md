# android-pr-review

**Senior Android / Kotlin / Java PR Code Review Skill**

A high-quality, well-calibrated code review skill designed for real engineering teams.

## What it does

Performs realistic senior-engineer code reviews with:

- Clear severity classification (Blocker / Should Fix / Nit / Informational)
- Strong anti-nitpicking calibration rules
- Mentoring, respectful tone that acknowledges good work
- Smart output formatting (lightweight unless there are real issues)
- Deep knowledge of modern Android, Kotlin, Jetpack Compose, coroutines, architecture, and security

## GitHub Superpowers

When GitHub is connected, this skill can:
- Automatically fetch the real diff of a PR (`owner/repo` + PR number or URL)
- Help you post full reviews or precise inline comments directly on the PR

## Trigger examples

- "Review this PR as senior Android engineer"
- "Do a code review on this Kotlin diff"
- "PR review #142 in my-org/my-app"
- "Analyze this Compose change for issues"

## Files

- `SKILL.md` — The complete skill definition (load this into your AI agent)
- `README.md` — This file

## Why it's good

Most generic "review my code" prompts either nitpick too much or miss important issues. This one is deliberately calibrated to give high-signal feedback that teams actually want to receive and act on.

## License

MIT

---

*Contributed as the first skill in the ai-skills repository.*

## Input / Output Contract (for humans)

**Inputs accepted:** GitHub PR URL (including /changes views), `owner/repo#N`, or raw diff text.

**Validation:** URLs are parsed safely (github.com only); owner/repo/pullNumber are range/pattern validated; raw diffs are detected by markers. Out-of-schema input produces a structured error and aborts.

**Primary outputs:** Severity-classified findings (markdown table or lightweight list) + (when real issues exist) structured JSON findings + optional raw "AI Agent prompt" for follow-up fixes.

**Maximum output size:** 10,000 characters for the complete findings output (table/list + JSON + agent prompt). Prioritizes all Blockers/Should-Fix; truncates lower severity with note.

**Scope — can:** Read PR metadata/diffs/comments via connected GitHub tools; post at most one review (or set of inline comments) on the single target PR per invocation.

**Scope — cannot:** Merge, close, approve without confirmation, push commits, modify source files, or act on any PR other than the referenced one.

**Dependencies:** Connected GitHub MCP tools (pull_request_read, search_connected_tools, pull_request_review_write, add_comment_to_pending_review).

See SKILL.md for the full review process. See references/CONTRACT.md and references/EVALUATIONS.md for the complete machine-readable contract and test cases.