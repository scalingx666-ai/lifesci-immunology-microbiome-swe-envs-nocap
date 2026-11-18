# Issue

**Title:** Limit how far locf_impute carries values forward

## Description

`ep.pp.locf_impute` gains `limit`, the maximum number of timepoints an observed value is carried forward, and its fallback only fills timepoints before a patient's first observation. Without a limit the results are unchanged; with one, longer gaps stay missing instead of being filled with the mean.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b27d57ecae7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.