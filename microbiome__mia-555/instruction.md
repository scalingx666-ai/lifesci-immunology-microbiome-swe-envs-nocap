# Issue

**Title:** Add explanation to rarefyAssay man page

## Description

This PR aims to explain that `rarefyAssay` returns a new `SummarizedExperiment` object that includes the original `counts` assay and the newly added subsampled assay. The goal is that the user is not mistaken thinking that the subsampled assay replaces the original `counts` assay.

It was already mentioned at the line documenting the `name` parameter but I tried to make it clearer.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ceb70fc31bd0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.