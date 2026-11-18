# Issue

**Title:** BUG: Remove rawgit and a bit of jQuery

## Description

- We use jsdelivr instead of rawgit which has better support for
  versioning, etc.

- The style template needed jQuery but some distributions, such as Voilá,
  would not make jQuery available making this template crash.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `406e043622e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.