# Issue

**Title:** LDA ordination with feature loadings computation

## Description

This PR adds two new methods `getLDA` and `addLDA` that perform Latent Dirichlet Allocation.

`getLDA` returns the ordination matrix with the feature loadings matrix stored as attribute.
`addLDA` adds this ordination matrix to `reducedDims` of the TreeSummarizedExperiment.

This PR is related to issue

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96bddb77c17b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.