# Issue

**Title:** cleanup for Stan draw files

## Description

- Introduced `cleanup_draw_files` parameter in `sccomp_estimate()` and `sccomp_remove_outliers()` to automatically delete large Stan draw CSV files after analysis, reducing disk space usage.
- Added new `clear_draw_files()` function for manual cleanup of draw files with flexible filtering options.
- Updated documentation and NEWS file to reflect these changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f20f96fc84d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.