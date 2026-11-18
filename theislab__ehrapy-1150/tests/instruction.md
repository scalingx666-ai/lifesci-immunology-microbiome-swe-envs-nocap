# Issue

**Title:** Summarize measurements by count, standard deviation and slope

## Description

`ep.pp.summarize_measurements` gains the statistics `"count"`, `"std"` and, for longitudinal data, `"slope"`, the least-squares change per timepoint. These are standard longitudinal features for stratification and prediction, and they work on numpy, sparse and dask arrays like the existing statistics.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b27d57ecae7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.