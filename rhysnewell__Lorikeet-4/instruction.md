# Issue

**Title:** Update install procedures.

## Description

Small changes. I'm not sure installing into your conda prefix is normal is it? I think most people would not actually install it (just build) if they were going from scratch.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b003d1295d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.