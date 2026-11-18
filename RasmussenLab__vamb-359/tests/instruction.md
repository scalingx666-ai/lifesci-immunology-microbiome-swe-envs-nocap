# Issue

**Title:** Set default taxometer batch steps to no steps

## Description

The previous defaults were conflicting, since the default number of epochs was smaller than the last steps.
Previous runs have indicated that no steps is a good option, though I believe we have never done any optimization on this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9810ef047ef4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.