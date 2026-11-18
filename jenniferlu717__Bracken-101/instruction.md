# Issue

**Title:** Recreate database if file exists but is empty.

## Description

If something went wrong during a previous attempt of `bracken-build`, `database.kraken` can be empty. If it is not created in that case, `bracken-build` will just create an empty database, which in turn causes errors such as Issue #99.

This avoids this by checking not only for the existence of `database.kraken` but also whether it is not empty.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5bf129ee219`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.