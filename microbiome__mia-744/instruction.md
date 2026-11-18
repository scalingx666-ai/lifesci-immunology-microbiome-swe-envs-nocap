# Issue

**Title:** Initialise agglomerateByModule

## Description

Basic agglomerateByModule function leveraging cross-product was initialised for SummarizedExperiment class.

Consider whether we should:
- [x] Add separate method for TreeSE
- [x] Add support for sample modules in colData
- [x] Integrate more with existing agglomerate and merge functions

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5bcb89d2f926`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.