# Issue

**Title:** Update tree agglomeration

## Description

1.
Add tree agglomeration to `subsetByPrevalent()` and `subsetByRare()`.  Fixes this issue: 

2.
Update the tree agglomeration; we used own implementation in `agglomerateBy*()` functions but now we utilize `TreeSummarizedExperiment::subsetByLeaf()`. Own implementation is still used in functions that handle matrix and tree, not `TreeSE` object.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `161b2096a2ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.