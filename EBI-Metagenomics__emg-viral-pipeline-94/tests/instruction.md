# Issue

**Title:** Re-build the virsorter container, using one hosted in quay by our team.

## Description

Added 2 more cwl test for virsorter to cover this case and to avoid regressions in the future.

We need to port the tests to nextflow.. not sure how yet.

This PR will fix

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47df4e408669`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.