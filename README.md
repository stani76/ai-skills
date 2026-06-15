# ai-skills

A curated collection of high-quality, reusable skills for AI Agents (Grok, Claude Projects, Cursor, Windsurf, GitHub Copilot CLI, etc.).

## Purpose

Collect battle-tested skills that encode expert workflows so agents can perform complex tasks reliably.

## Repository Structure

```
github/                     # GitHub-related skills
  └── android-pr-review/     # Senior Android/Kotlin/Java PR reviewer with Copilot CLI support
```

## Key Skills

### android-pr-review

**Senior Android / Kotlin / Java PR Code Review Skill**

Fully calibrated for real teams. Supports slash command `/android-pr-review` in GitHub Copilot CLI.

**Usage:**

```
/android-pr-review
/android-pr-review Review focusing on performance and security
```

Features:
- Calibrated severity (Blocker/Should Fix/Nit/Informational)
- Strict anti-nitpicking rules
- Mentoring tone
- GitHub PR diff fetching + review posting
- Deep Android/Kotlin/Compose expertise

[Details →](github/android-pr-review/README.md)

## Contributing

Add skills in category folders (e.g. `github/`). Each skill needs a `SKILL.md` with proper YAML frontmatter (`name` + `description`).

For Copilot CLI compatibility, the `name` field sets the slash command (e.g. `/android-pr-review`).

## About

A repo for skills to use in AI Agents