# Issue

**Title:** Fix getMediation bug

## Description

Fixing behaviour of getMediation for following example:

```
library(mia)
library(scater)

# Load dataset
data(hitchip1006, package = "miaTime")
tse <- hitchip1006

# Agglomerate features by family (merely to speed up execution)
tse <- agglomerateByRank(tse, rank = "Phylum")
# Convert BMI variable to numeric
tse$bmi_group <- as.numeric(tse$bmi_group)

# Analyse mediated effect of nationality on BMI via alpha diversity
# 100 permutations were done to speed up execution, but ~1000 are recommended 
med_df <- getMediation(tse,
                       outcome = "bmi_group",
                       treatment = "nationality",
                       mediator = "diversity",
                       covariates = c("sex", "age"),
                       treat.value = "Scandinavia",
                       control.value = "CentralEurope",
                       boot = TRUE, sims = 100,
                       add.metadata = TRUE)
```

Current version returns error (Error: The arguments mediator, assay.type and dimred are mutually exclusive, but 2 were provided), introduced with .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8e1e0a929d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.