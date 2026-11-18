# Issue

**Title:** [fix] keep match with highest score

## Description

Fixes the sorting of matches.
Before lambda3 sorted the matches and outputted the first entry, which wasn't always the match with the highest score.

This additionally sorts by the inverted bitScore to ensure that `unique` keeps the match with the highest score.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f504f69c7142`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.