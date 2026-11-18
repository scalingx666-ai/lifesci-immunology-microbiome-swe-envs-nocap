# Issue

**Title:** Give informative error when values are missing in addRDA

## Description

Fix for issue 

Usage examples:

```
# Import TreeSE
library(mia)
data("enterotype", package = "mia")
tse <- enterotype

# Throw error when na.action is na.fail and some values are missing

tse <- addCCA(tse, formula = assay ~ ClinicalStatus + Gender + Age)
# Error: Variables contain missing values. Set na.action to na.exclude to remove
# samples with missing values.

tse <- addRDA(tse, formula = assay ~ ClinicalStatus + Gender + Age,
              FUN = vegan::vegdist, method = "bray")
# Error: Variables contain missing values. Set na.action to na.exclude to remove
# samples with missing values.

# Work as usual when na.action is na.omit or na.exclude

tse <- addCCA(tse, formula = assay ~ ClinicalStatus + Gender + Age,
              na.action = na.exclude)

tse <- addRDA(tse, formula = assay ~ ClinicalStatus + Gender + Age,
              FUN = vegan::vegdist, method = "bray",
              na.action = na.exclude)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `586392f56285`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.