# Issue

**Title:** Apply transformation only to main object by default

## Description

Applying `transformAssay` to alternative experiments might lead to error that can be hard to solve.

> Error: 'assay.type' must be a valid name of assays(x)

This comes from the alternative experiment that did not have an assay named `assay.type` even though the main object had.

That is why transformation is not applied to alternative experiments by default. Moreover, the experiments can include data that is not from same source, meaning that similar transformation might not be well justified (for instance, metagenomics vs metabolites)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b316373ae2f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.