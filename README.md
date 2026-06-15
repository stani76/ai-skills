# ai-skills

A curated collection of high-quality, reusable skills for AI Agents (Grok, Claude Projects, Cursor, Windsurf, GitHub Copilot CLI, etc.).

## Purpose

Collect battle-tested skills that encode expert workflows so agents can perform complex tasks reliably.

## Repository Structure

```
github/                     # GitHub-related skills
  └── android-pr-review/     # Senior Android/Kotlin/Java PR reviewer
```

## Key Skills

### android-pr-review

**Senior Android / Kotlin / Java PR Code Review Skill** — Fully compatible with GitHub Copilot CLI slash command `/android-pr-review`.

Invocable directly with:

```
/android-pr-review
/android-pr-review Review this PR focusing on Compose and security
```

Features calibrated severity levels, excellent anti-nitpicking rules, GitHub integration (fetch diff + post reviews), deep Android/Kotlin expertise, and mentoring tone.

[Details →](github/android-pr-review/README.md)

## Contributing

Add skills in category folders (e.g. `github/`). Each skill needs a `SKILL.md` with proper YAML frontmatter (`name` + `description`).

For Copilot CLI compatibility, the `name` in frontmatter determines the `/slash-command`.

## About

A repo for skills to use in AI Agents