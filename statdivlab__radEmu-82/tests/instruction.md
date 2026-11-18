# Issue

**Title:** Allow users to input data with a TreeSummarizedExperiment object

## Description

This responds to issue #64, wherein we decided to allow users to input `TreeSummarizedExperiment` objects, in response to continued errors from the `phyloseq` package. This currently implements the core functionality, without consideration to using `radEmu` after aggregating `TreeSummarizedExperiment` objects.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cae1f1816344`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.