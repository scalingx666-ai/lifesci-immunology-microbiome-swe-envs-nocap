# Issue

**Title:** Rename estimateDivergence to addDivergence

## Description

This PR makes the following naming modifications : 

- `estimateDivergence` --> `addDivergence`

The manual page `estimateDivergence` becomes `addDivergence` to avoid duplicated aliases between files `estimateDivergence.Rd` and `deprecate.Rd`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1adf43c1e8de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.