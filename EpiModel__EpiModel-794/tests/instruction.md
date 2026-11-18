# Issue

**Title:** Fix error where `get_attr_history` would crash on length zero PIDs

## Description

- using `dplyr::as_tibble` fixes it automatically
- addition of a specific test for the 0 length case

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `305afac5f3da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.