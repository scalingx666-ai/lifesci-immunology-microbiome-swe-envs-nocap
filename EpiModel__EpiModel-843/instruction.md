# Issue

**Title:** add delete_edges, update trim_netest

## Description

This PR also standardizes the test for whether or not a model "is a tergm" by checking if the first durational target is > 1 or = 1.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd9c8211af85`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.