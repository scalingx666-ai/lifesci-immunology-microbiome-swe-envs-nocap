# Issue

**Title:** Temporarily disable manuscript stats

## Description

The external resources build failed https://github.com/greenelab/covid19-review/runs/3593275250?check_suite_focus=true

I believe I know how to fix this by using an action to checkout the output branch.  I'll work on it post DISCO-submission.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ca9e1a3926e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.