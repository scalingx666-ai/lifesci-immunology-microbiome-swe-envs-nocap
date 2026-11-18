# Issue

**Title:** Stop flipping censor_flg in the survival examples

## Description

The survival docstring examples no longer flip `censor_flg` of MIMIC-II, which `ed.dt.mimic_2` already codes as 1 for death, so that they model the time to death instead of the time to censoring.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf51fd095f83`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.