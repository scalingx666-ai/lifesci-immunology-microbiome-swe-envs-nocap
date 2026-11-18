# Issue

**Title:** Fix pkgdown error

## Description

Right now pkgdown checks are failing with an error related to an object class used by `SummarizedExperiment` and `TreeSummarizedExperiment` - try to resolve this

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df415c5020f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.