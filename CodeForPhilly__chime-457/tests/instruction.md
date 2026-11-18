# Issue

**Title:** Iteratively refined fitting

## Description

Fixes: #449 

At least as close as it reasonably can be without lighting servers on fire.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19fe67584c37`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.