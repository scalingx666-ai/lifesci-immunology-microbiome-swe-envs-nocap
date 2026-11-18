# Issue

**Title:** Staging

## Description

This pull request updates GTDB-Tk to version 2.7.2. The main changes include fixing a bug related to the "warning_counter" error during bacterial backbone reference tree placement, removing the `--skip_ani_screen` option from the `test` command, and updating documentation to reflect these changes and clarify installation instructions.

**Version Bump:**
* Updated the package version to `2.7.2` in `__init__.py`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7c7e90e91df0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.