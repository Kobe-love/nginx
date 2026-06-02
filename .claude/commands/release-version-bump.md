---
name: release-version-bump
description: Workflow command scaffold for release-version-bump in nginx.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /release-version-bump

Use this workflow when working on **release-version-bump** in `nginx`.

## Goal

Performs a new release by updating the changelog and bumping the version number in the core header.

## Common Files

- `docs/xml/nginx/changes.xml`
- `src/core/nginx.h`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update release notes in docs/xml/nginx/changes.xml
- Bump version number in src/core/nginx.h

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.