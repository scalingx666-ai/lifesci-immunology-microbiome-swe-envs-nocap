# Issue

**Title:** add informative error message for strictly-negative values in rarefyAssay

## Description

Assays with strictly-negative values are not handled by `rarefyAssay`.
```
data(GlobalPatterns)
tse <- GlobalPatterns
matrix <- assay(tse)
matrix[1,1] <- -1
assay(tse) <- matrix
rarefyAssay(tse)
```
>Error in sample.int(length(x), size, replace, prob) : 
  negative probability

This PR adds an informative error message.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9198263a0f88`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.