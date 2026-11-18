# Issue

**Title:** BUG: Fix bug with axis inversion in settings

## Description

An axis would only be inverted if the loaded setting was "True", however
this would not honor the inversions that needed to happen if an axis was
currently set to True but should be changing to False.

I've included a unit test for this bug.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `067c4178cc33`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.