# Issue

**Title:** fix: return mergeList if it is already a SummarizedExperiment

## Description

This PR fixes issue #321 where calling mergeData on a TreeSummarizedExperiment fails. It also adds a unit test.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a97706cfad6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.