# Issue

**Title:** chore: release 0.6.1

## Description

The version line of the 0.6.1 branch, the release that merges back the five commits since v0.6.0: the python 3.14 and scaling batch (f42ed03), the lineage/opener/licence batch (82f5c12), the answered user questions #71 and #74 (2ba41b0), the tree consistency rules of #162 (baff977) and the digit-named nodes of #161 (80125dd). 154 tests pass.

Backup: flextaxd/.fix-backups/2026-11-12-1614-release-061-version

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33ca29b62a21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.