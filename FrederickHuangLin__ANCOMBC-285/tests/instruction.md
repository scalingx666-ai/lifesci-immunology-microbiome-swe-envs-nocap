# Issue

**Title:** bug fix for ancombc2 when a similar function with model.matrix function is loaded from AlgDesign package

## Description

When the AlgDesign package is loaded, its model.matrix function interferes with the model.matrix from the stats package used in the ancombc2 function, making it unable to recognize data formats similar to data.frame. It is fixed by using stats::model.matrix to avoid wrong call.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e97abeaf1896`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.