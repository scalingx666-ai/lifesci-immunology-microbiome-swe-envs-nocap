# Issue

**Title:** Fix mcar_test crash on 3D data with a single timepoint

## Description

- squeeze the trailing single time axis after resolving `mtx`, mirroring what `function_2D_only()` already tolerates
- updated the docstring's expected output, which changes as a result

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4631d5715105`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.