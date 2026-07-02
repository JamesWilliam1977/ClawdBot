---
name: refresh-ui-locale-metadata
description: Workflow command scaffold for refresh-ui-locale-metadata in ClawdBot.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /refresh-ui-locale-metadata

Use this workflow when working on **refresh-ui-locale-metadata** in `ClawdBot`.

## Goal

Refreshes or updates the UI locale metadata for a specific language, keeping translations and locale information up to date.

## Common Files

- `ui/src/i18n/.i18n/*.meta.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or regenerate the locale meta JSON file for a specific language in ui/src/i18n/.i18n/
- Commit the change with a message indicating the locale refreshed

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.