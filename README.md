# ai-skills

A curated repository of high-quality skills for AI coding agents (Grok, GitHub Copilot CLI, Claude, Cursor, etc.).

## Available Skills

### android-pr-review

**Senior Android / Kotlin / Java PR Code Reviewer**

A well-calibrated, realistic code review skill that acts like an experienced team lead.

#### Installation (GitHub Copilot CLI)

```bash
# Install the skill directly
gh skill install stani76/ai-skills android-pr-review
```

#### Usage in Copilot CLI

```bash
/android-pr-review
/android-pr-review Review this PR focusing on Compose and security
```

#### Other Agents

- Copy the `github/android-pr-review/` folder into your agent's skills directory (e.g. `~/.copilot/skills/` or `.github/skills/`). 
- Trigger naturally: "Review this PR as senior Android engineer"

See full details in [github/android-pr-review/README.md](github/android-pr-review/README.md)

## Contributing

Feel free to add more skills following the same structure. PRs welcome!

## License

MIT
