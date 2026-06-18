# Contract for android-pr-review

This document defines the skill's contract, including input and output schemas, scope boundaries, and operational constraints, to align with industry standards for agent skills.

## Input Schema

Accepted forms:
- GitHub PR URL (e.g. `https://github.com/owner/repo/pull/123` or the changes view `.../pull/123/changes/<sha>`)
- Shorthand `owner/repo#N` or `owner/repo pull N`
- Raw diff text (pasted unified diff or full page contents from a diff view)

### Validation Rules (enforced before any tool use or heavy processing)
- If input contains a GitHub URL:
  - Parse safely. Host must be exactly `github.com`.
  - Path must match PR form (`/pull/{number}` or `/pull/{number}/changes/...`).
  - Reject on traversal (`..`), non-github hosts, or suspicious elements.
- After extraction (or for shorthand):
  - `owner` matches: `^[a-zA-Z0-9]([a-zA-Z0-9-]{0,37}[a-zA-Z0-9])?$`
  - `repo` matches: `^[a-zA-Z0-9_.-]{1,100}$`
  - `pullNumber` matches: `^[1-9][0-9]*$`
- For raw text: if it contains unified diff markers (`diff --git`, `--- a/`, `+++ b/`, or `@@ ` hunks), treat as raw diff input.
- Failure at any step: emit structured error (e.g. `{"error": "InvalidInput", "message": "description", "field": "owner"}`) and abort. Never call tools or proceed silently.

Parameter types: owner (string), repo (string), pullNumber (positive integer), rawDiff (string).

## Output Schema + Maximum Output Size

When Blockers or Should-Fix exist:
- Markdown table (Severity | Line | Code | Issue | Suggested Fix)
- Raw markdown "AI Agent prompt" (mentoring/fix instructions)
- Structured JSON version of the findings (see below) — provided automatically if the user requests it at the start, or offered at the end otherwise.

When only Nits/Informational:
- Lightweight bullet list
- Explicit statement: "No agent prompt is required — none of these observations should gate merge."
- No JSON or agent prompt

When clean:
- "✅ This PR meets best practices. No issues found — approved."

**Maximum output size:** 10,000 characters for the complete findings output (table/list + JSON + agent prompt if present).

Truncation rule:
- Always include every 🔴 Blocker and 🟠 Should Fix.
- Include at most the first 10 🟡 Nits / 🟢 Informational (highest impact first).
- If truncated, append exactly: "(Output truncated due to size limit. X additional lower-severity findings omitted. Address the listed issues first.)"

### Structured JSON Schema (when offered)
```json
{
  "findings": [
    {
      "severity": "Blocker" | "Should Fix" | "Nit" | "Informational",
      "file": "relative/path/ToFile.kt",
      "line": 42,
      "code": "exact snippet or null",
      "issue": "clear one-sentence description of the problem",
      "suggested_fix": "actionable suggestion or null"
    }
  ],
  "truncated": false,
  "omitted_count": 0
}
```
- Use severity labels without emoji.
- `line` is integer (or null for file-level).
- JSON respects the same 10k-char cap and truncation logic.

## Scope — Can / Cannot

**Can:**
- Read PR metadata, diffs, commits, review comments, and status via connected GitHub tools.
- Perform the full calibrated review (severity table, JSON, agent prompt where appropriate).
- Help draft or post review comments / inline suggestions on the single target PR.
- At most: one overall review + associated inline comments per invocation.

**Cannot:**
- Merge, close, or update the PR status.
- Approve without explicit user confirmation.
- Push commits or modify source files.
- Act on any PR other than the one referenced in the current input.
- Execute arbitrary code or access resources outside the declared GitHub tools.

## Max Scope of Writes
At most one review (with event APPROVE / REQUEST_CHANGES / COMMENT) or set of inline comments on the single target PR per invocation.

## Abort Conditions
- Connected GitHub tools unavailable.
- Input fails validation (invalid owner/repo/pullNumber, non-GitHub URL, no diff markers when expected, etc.).
- Diff exceeds practical processing limits (agent should fall back to high-level summary per Large PRs guidance).
- Any attempt to perform out-of-scope actions (merge, multi-PR, etc.).

## Idempotency
Posting a review or comments is **not idempotent**.

Before any write:
- Call `pull_request_read` (get_reviews or get_review_comments).
- Check for prior reviews/comments containing the marker "android-pr-review v1.0.0" or the table header "Severity | Line | Code | Issue | Suggested Fix".
- If found, report the prior run and require explicit confirmation before posting a duplicate.

## Dependencies
- GitHub MCP tools (short names declared in frontmatter): `pull_request_read`, `search_connected_tools`, `pull_request_review_write`, `add_comment_to_pending_review`.
- The agent discovers concrete tool names at runtime via `search_connected_tools` (query containing "github" and "pull_request_read" or "pr").

Version: 1.0.0
