# ai-skills

A curated collection of high-quality, reusable skills for AI Agents (Grok, Claude Projects, Cursor, Windsurf, etc.).

## Purpose

Collect battle-tested skills that encode expert workflows, domain knowledge, and tool integrations so agents can perform complex tasks reliably and consistently.

## Repository Structure

```
skills/               # (future) General or cross-platform skills

github/                # Skills that interact with GitHub (PR reviews, issues, automation, etc.)
  └── android-pr-review/   # Senior Android/Kotlin/Java PR reviewer with GitHub integration
```

## Available Skills

### `github/android-pr-review`

**Senior-level code review for Android, Kotlin & Java PRs**

- Calibrated severity levels + excellent anti-overreporting rules
- Mentoring tone + smart conditional output format
- Strong Android/Kotlin/Compose/coroutines knowledge
- **Native GitHub support**: fetch real PR diffs and post reviews/comments directly

**Quick start:** Tell your agent "Use the android-pr-review skill to review this PR..." or "Do a senior PR review on PR #123 in owner/repo".

Full details: [github/android-pr-review/README.md](github/android-pr-review/README.md)

## Contributing

We welcome high-quality skills!

1. Create a new folder under the appropriate category (e.g. `github/`, `linear/`, or top-level for general skills)
2. Add at minimum a `SKILL.md` file following the standard skill frontmatter + instructions format
3. Optionally add a `README.md` explaining usage and value
4. Open a Pull Request with a clear description

Skills should be practical, well-calibrated, and solve real recurring problems for AI agent users.

## License

MIT
