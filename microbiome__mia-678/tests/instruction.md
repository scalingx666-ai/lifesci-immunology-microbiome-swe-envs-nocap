# Issue

**Title:** Polish mediation model metadata

## Description

Hi! This PR targets the messy metadata of the getMediation output and reorganises it into a data.frame. This issue was raised in 

Example:
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

# Apply clr transformation to counts assay
tse <- transformAssay(tse,
                      method = "clr",
                      pseudocount = 1)

# Analyse mediated effect of nationality on BMI via clr-transformed features
# 100 permutations were done to speed up execution, but ~1000 are recommended
tse <- addMediation(tse, name = "assay_mediation",
                    outcome = "bmi_group",
                    treatment = "nationality",
                    assay.type = "clr",
                    covariates = c("sex", "age"),
                    treat.value = "Scandinavia",
                    control.value = "CentralEurope",
                    boot = TRUE, sims = 10,
                    p.adj.method = "fdr")

med_df <- metadata(tse)[["assay_mediation"]]
metadata_df <- attr(med_df, "model metadata")

dim(metadata_df)
> [1]  8 56

names(metadata_df)
 [1] "d0"            "d1"            "d0.ci"         "d1.ci"         "d0.p"         
 [6] "d1.p"          "d0.sims"       "d1.sims"       "z0"            "z1"           
[11] "z0.ci"         "z1.ci"         "z0.p"          "z1.p"          "z0.sims"      
[16] "z1.sims"       "n0"            "n1"            "n0.ci"         "n1.ci"        
[21] "n0.p"          "n1.p"          "n0.sims"       "n1.sims"       "tau.coef"     
[26] "tau.ci"        "tau.p"         "tau.sims"      "d.avg"         "d.avg.p"      
[31] "d.avg.ci"      "d.avg.sims"    "z.avg"         "z.avg.p"       "z.avg.ci"     
[36] "z.avg.sims"    "n.avg"         "n.avg.p"       "n.avg.ci"      "n.avg.sims"   
[41] "boot"          "boot.ci.type"  "treat"         "mediator"      "covariates"   
[46] "INT"           "conf.level"    "model.y"       "model.m"       "control.value"
[51] "treat.value"   "nobs"          "sims"          "call"          "robustSE"     
[56] "cluster"

View(metadata_df)
```

![Screenshot 2025-01-21 at 15 13 34](https://github.com/user-attachments/assets/75be5fa3-a807-4b37-90b1-bf77f90ea7b2)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f80ea321d1a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.