# Issue

**Title:** Fix roxygen documentation for files return value in clear_draw_files

## Description

Addresses review feedback to update roxygen comments in source file rather than generated .Rd file.

## Changes

- Updated `@return` documentation in `R/clear_draw_files.R` to clarify `files` field behavior:
  - `dry_run = TRUE`: files that would be deleted
  - `dry_run = FALSE`: files that were successfully deleted

Previously stated "Vector of deleted file paths (if dry_run = FALSE)" which was misleading since the field is returned in both modes with different semantics.

<!-- START COPILOT CODING AGENT TIPS -->
---

💡 You can make Copilot smarter by setting up custom instructions, customizing its development environment and configuring Model Context Protocol (MCP) servers. Learn more [Copilot coding agent tips](https://gh.io/copilot-coding-agent-tips) in the docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60054d32a553`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.