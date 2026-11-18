# Issue

**Title:** Fix arg parsing issue

## Description

Latest release introduced an issue with any subcommand that does not read in the QC argument group. Causes immediate crash and needs to be fixed up with a new minor release imo

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2c61ba1df83b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.