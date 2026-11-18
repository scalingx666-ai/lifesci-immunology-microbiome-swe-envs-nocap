# Issue

**Title:** NMF ordination with feature loadings computation

## Description

This PR adds two new methods `getNMF` and `addNMF` that perform Non-negative Matrix Factorization.

`getNMF` returns the ordination matrix with the feature loadings matrix and NMF model stored as attributes.
`addNMF` adds this ordination matrix to `reducedDims` of the TreeSummarizedExperiment.

This PR is related to issue

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c00541b64042`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.