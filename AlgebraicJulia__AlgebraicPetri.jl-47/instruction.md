# Issue

**Title:** CompatHelper: bump compat for "Catlab" to "0.12"

## Description

This pull request changes the compat entry for the `Catlab` package from `^0.11.0` to `^0.11.0, 0.12`.

This keeps the compat entries for earlier versions.

Note: I have not tested your package with this new compat entry. It is your responsibility to make sure that your package tests pass before you merge this pull request.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b031075b6008`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.