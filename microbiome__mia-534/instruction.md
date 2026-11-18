# Issue

**Title:** Rename meltAssay to meltSE

## Description

This PR makes the following naming modifications : 

- `meltAssay` --> `meltSE`

The manual page meltAssay becomes meltSE to solve R cmd check warning about duplicated alias `meltAssay`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3931f7477d7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.