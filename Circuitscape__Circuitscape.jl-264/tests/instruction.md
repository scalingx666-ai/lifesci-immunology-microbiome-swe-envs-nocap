# Issue

**Title:** Use do-blocks for managing rasters via ArchGDAL

## Description

That way you clean up the `raw` dataset even in the event of an error.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d5258c43a55a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.