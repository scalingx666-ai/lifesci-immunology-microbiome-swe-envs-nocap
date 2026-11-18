# Issue

**Title:** Consolidate arguments checking in accessors

## Description

- single `assert_valid_posit_ids` function shared among accessors
- single `assert_valid_time_steps` function shared among accessors
- removal of logical subsetting in accessors
- code reformatting for consistency with the rest of the codebase
- update the tests to reflect the changes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5340bf31d8bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.