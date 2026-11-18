# Issue

**Title:** Address issue #38, a vignette for using radEmu with clustered data (take two)

## Description

This pull request does the following:

- updates `emuFit()` to take in the any kind of vector as the `cluster` argument
- check that all of the different inputs to cluster provide the same results
- add the first draft of a vignette explaining how to use the cluster argument and why we want to account for data with cluster dependence

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26dc3354dafa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.