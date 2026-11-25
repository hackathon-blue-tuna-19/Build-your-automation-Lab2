---
name: repo-summary
description: Summarize all recent updates to the repository in natural language. Use when asked what changed, for a repo summary, changelog, or catch-up on recent activity.
---

# Repo summary

Explain what has changed in this repository in plain, readable language.

1. Pick the time window. Use the one given; otherwise default to the last 7 days.
2. Gather updates with read-only commands (use `GH_REPO=<owner/repo>` or `-R` when
   the target is not the current checkout):
   - `git --no-pager log --since="<window>" --no-merges --stat --format='%h %an %s'`
   - `gh pr list --state all --search "updated:>=<date>" --json number,title,state,author`
   - `gh issue list --state all --search "updated:>=<date>" --json number,title,state`
3. Group related changes into themes (features, fixes, docs, tooling) instead of
   listing commits one by one.
4. Write the summary:
   - A 2–3 sentence overview of what happened.
   - A short paragraph or bullets per theme, linking PRs and issues as `#<number>`.
   - A closing line on open work (unmerged PRs, open issues) if any.
5. If nothing changed in the window, say so plainly.

## Rules

- Never modify the repository, branches, issues, or pull requests.
- Never invent changes; only report what the commands returned.
- Don't paste raw diffs or commit hashes unless asked; keep it natural language.
- Don't include secrets or private data that appear in output.
