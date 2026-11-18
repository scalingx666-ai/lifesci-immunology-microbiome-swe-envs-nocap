# Issue

**Title:** Debug/pathofact2

## Description

Pathofact2 doesn't like characters representing unknown aminoacids (X). We added code to remove those proteins with such aminoacids.

Thanks for reviewing!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e9c8f313584`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.