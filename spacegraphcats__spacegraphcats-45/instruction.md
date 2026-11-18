# Issue

**Title:** Graph tests

## Description

This addresses issue #43: the TFGraph class and the code to compute dominating sets are now tested with random graph instances and some small hand-crafted cases. The dominating set code contains more comments, however, without knowledge of the underlying algorithms/data-structures even these will probably not help.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac4cdd39d9d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.