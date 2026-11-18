# Issue

**Title:** Reorganize and improve tests

## Description

Related to #31: this is a major rewrite of the test suite. Each test is now its own function, allowing tests to be run individually if desired (should speed up testing considerably!). Tests are also categorized, allowing for repo-specific tests to be run as a group. This PR does not change any core grabseqs functionality, only the tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ceca1a6d39b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.