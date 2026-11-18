# Issue

**Title:** Allow both manual and automatic randomization of agents ordering

## Description

By default, the random reordering happens at the end of every iterations (during the teardown operation), but with this PR this can be turned off by initializing the `auto_randomize_` variable of the `RandomizedRm` class with `false`. To manually trigger the random reordering of agents, you can call the `RandomizedRm::RandomizeAgentsOrder` function.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `137fdb1523c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.