# Issue

**Title:** Keep logarithmic overlap distances nonnegative for clustering

## Description

Identical repertoires can produce −4.34e−10 off-diagonal distances because the legacy logarithmic transform adds 1e−9 before taking the logarithm. `cluster_samples(..., method="hclust")` then raises `ValueError: Linkage 'Z' contains negative distances`.

Floor logarithmic distances at zero in both the scalar and sparse-matrix paths. Positive distances retain their existing arithmetic; update the explanation and notebook formula.

Validation: all six new direct/batched F/F2/D regression cases fail before the fix and pass afterward, including actual hierarchical clustering. 140 focused tests pass, strict Sphinx and strict marimo checks pass. No native kernels or models change. Merge this fix before the pending 5.3.1 release promotion (#217).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `836c871f8a83`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.