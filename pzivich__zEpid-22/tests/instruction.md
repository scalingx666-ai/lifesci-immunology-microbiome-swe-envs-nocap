# Issue

**Title:** align on a single API for printing a model

## Description

Some small changes to the API for printing models: previously there were three different signatures, this fixes it to a single `print_results` (which is short and clear imo).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `988c4fa54de2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.