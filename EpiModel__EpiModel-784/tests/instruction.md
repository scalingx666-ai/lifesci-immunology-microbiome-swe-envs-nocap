# Issue

**Title:** fix rng and scenarios tests

## Description

- some of the rng params test where malformed they were adding duplicated params where they shouldn't. Triggering warnings that are tested elsewhere
- the check_scenario_df function was letting a warning pass due to poor ordering of the checks

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a19d2a98e53`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.