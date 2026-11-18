# Issue

**Title:** Nearest Neighbor Support

## Description

This pull request provides Nearest Neighbor support.

For similarity measures, such as Jaccard, histogram similarity, and containment, it returns the `k` greatest similarities and associated indexes.

For dissimilarity measures, such as distances, it returns the `k` lowest similarities with associated indexes.

It can be activated with the `--nearest-neighbor [number]` flag, and is available for both all pairs calculations (default/-F) and the query/reference interface (-Q/-F). Output format is either tabular (default), or, if `-b/--binary` is activated, a raw binary dump of the distances and indices.

Partially addressed  (nearest neighbors), but not thresholded output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e3a2208739f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.