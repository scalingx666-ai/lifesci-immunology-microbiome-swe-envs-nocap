# Issue

**Title:** Require megahit <1.2

## Description

This updates the conda environment file to require megahit below version 1.2.  I also added en explicit error message for a related test failure in test_all.  This .  I'd like to merge this straight into stable so new installs work as expected again; we can then update and finish off #204 and sync it all back with dev too.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6102f69097c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.