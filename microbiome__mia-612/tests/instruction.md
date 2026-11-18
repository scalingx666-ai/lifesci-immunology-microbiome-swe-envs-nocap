# Issue

**Title:** Fix addAlpha

## Description

addAlpha was failing with the following commands

```
data("GlobalPatterns")

tse <- GlobalPatterns

# This was not working
addAlpha(tse, index = "faith") |> colData()
addAlpha(tse, index = "faith", tree = rowTree(tse) ) |> colData()

se <- tse
rowTree(se) <- NULL
addAlpha(se, index = "faith", tree = rowTree(tse) ) |> colData()
addAlpha(se, index = "faith") |> colData()

se <- as(tse, "SummarizedExperiment")
rownames(se) <- rownames(tse)
addAlpha(se, index = "faith", tree = rowTree(tse) ) |> colData()
addAlpha(se, index = "faith") |> colData()
```

Now it is working. I also ensured that deprecated estimate* functions work after modifications.

The problem was related to calling .estimate_faith which was generic function. First TreeSE version of .estimate_faith was called and then the TreeSE version called SE version. However, there was missmatch, and (Tree)SE + phylo was not detected which caused an error.

The code -- especially faith calculation -- was very complex since both estimateDiversity (.estimate_diversity) and estimateFaith (.estimate_faith) were exported functions previously. As now all alpha measures are calculated with addAlpha, we can remove functionality that was related to exporting the function For instance, estimateFaith needed to work alone before; now the function is called from addAlpha -->.estimate_diversity, so it does not need all the functionality that exported functions need to have.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9012592700d3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.