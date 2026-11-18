# Issue

**Title:** Add R & dependencies to Dockerfile

## Description

Remove seqkit which is not used.

The `install.package` commands in the R scripts do not work when R is being run from the command line as they need the user to choose a mirror.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd75393957ef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.