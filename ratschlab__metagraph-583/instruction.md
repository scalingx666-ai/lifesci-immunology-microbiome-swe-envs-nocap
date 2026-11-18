# Issue

**Title:** Fix catching errors when lsof doesn't exist or fails

## Description

Previously, errors went unnoticed because of the piping `| tail -n +2 | wc -l`, and the function silently returned 0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c621f69ea5aa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.