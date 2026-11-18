# Issue

**Title:** Make argument `test_kj` required in `emuFit()` when `run_score_tests = TRUE`

## Description

updating `emuFit()` so that when `run_score_tests = TRUE`, the argument `test_kj` is required instead of optional. Noting this in the vignette, and updating tests to now use this behavior. Updating the package version number to reflect this breaking change (non-backwards compatible) and adding a news.md file to explain this and future version incrementations to users.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c36d7e0511f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.