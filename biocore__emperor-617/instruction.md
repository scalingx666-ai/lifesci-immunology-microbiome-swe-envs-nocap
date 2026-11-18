# Issue

**Title:** BUG: Fix bug where plot would rotate slightly

## Description

The controls only need to be updated if the rotation is enabled.

Merge #614 first, as it includes the version updates.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6df010ce08c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.