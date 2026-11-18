# Issue

**Title:** Improve support for spaces in variable names

## Description

I noticed that formula creation in dbRDA can lead to an error when variable names have spaces. Now it is ensured that, the formula works with spaces.

Moreover, `meltSE` replaced spaces with dots. Now the data is melted so that variable names are kept untouched.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fe852c046b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.