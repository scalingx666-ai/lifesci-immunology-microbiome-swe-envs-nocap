# Issue

**Title:** Add parameter to allow for sample order to be specified

## Description

Hi,

This pull request proposes a new parameter to the `reorder_samples_by` function that allows users to specify an order of samples for plotting.

- [x] Tested with Global Patterns vignette
- [x] Tested with HMP2 vignette 

For example, with the Global Patterns data:
```r
ps_human <- subset_samples(GlobalPatterns, SampleType %in% c("Skin", "Feces", "Tongue"))

mdf_human <- prep_mdf(ps_human, 
                      subgroup_level = "Genus")

color_objs_human <- create_color_dfs(mdf_human,
                                    selected_groups = c("Verrucomicrobia", "Proteobacteria", "Actinobacteria",
                                                        "Bacteroidetes", "Firmicutes"), 
                                    group_level = "Phylum",
                                    subgroup_level = "Genus",
                                    cvd = TRUE)

order <- c("M31Plmr", "F21Plmr", "M11Plmr", "M11Tong", "TS28", "TS29", "M11Fcsw", "M31Fcsw", "M31Tong")
reorder_samples_by(color_objs_human$mdf,
                  color_objs_human$cdf,
                  sample_ordering = order)
```
![image](https://github.com/KarstensLab/microshades/assets/90294056/ca4992ca-4fea-4d7c-9232-a322ac6a0a53)


Thanks!
-Anagha

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a30de3520e3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.