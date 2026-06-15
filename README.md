# ai-skills

A curated collection of high-quality, reusable skills for AI Agents (Grok, Claude Projects, Cursor, Windsurf, GitHub Copilot CLI, etc.).

## Purpose

Collect battle-tested skills that encode expert workflows so agents can perform complex tasks reliably.

## Repository Structure

```
github/                     # GitHub-related skills
  ├── pr-review/             # Senior PR reviewer — invocable as /pr-review in Copilot CLI
  └── android-pr-review/     # Detailed Android/Kotlin/Java focused version
```

## Key Skills

### `/pr-review` (github/pr-review)

**Senior PR Code Review skill** — Optimized for GitHub Copilot CLI slash command.

Invocable directly with:
```
/pr-review
```

Features calibrated severity levels, excellent anti-nitpicking rules, GitHub integration (fetch diff + post reviews), and deep Android/Kotlin expertise.

Perfect default PR reviewer for teams working with Android or modern Kotlin.

[Details →](github/pr-review/README.md)

### android-pr-review

The original detailed version under the longer name.

[Details →](github/android-pr-review/README.md)

## Contributing

Add skills in category folders (e.g. `github/`). Each skill needs a `SKILL.md` with proper YAML frontmatter (`name` + `description`).

For Copilot CLI compatibility, the `name` in frontmatter determines the `/slash-command`.
