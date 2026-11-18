# Issue

**Title:** Create RefHasher type

## Description

When only the Abundance type used refhashing, we could get away with it only being a simple function. However, now that I want marker gene prediction to also use refhashing, the existing implementation did not work, and I would need to have two differing implementation that absolutely needed to give the same result.

Instead, make a RefHasher type such that the invariants are stored in one place, and also generalize the error message improvement from commit 37277e2.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37277e23fa1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.