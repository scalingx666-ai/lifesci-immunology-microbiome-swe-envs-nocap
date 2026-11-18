# Issue

**Title:** Se support

## Description

This pull request adds support for the (Tree)SummarizedExperiment class. Feedback from previous pull request has been implemented. I tested that outcomes of ancombc function are equal between using pseq or tse using the atlas dataset. And currently: Yes they are equivalent but the sorting of the rownames (taxa names) is altered in tse compared to pseq. This has however no influence on the results (pvalues, betas etc.). The sorting changes when converting from pseq to tse. So this is not something to address further here.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ceb5ad5f595e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.