# Issue

**Title:** Fix rownames="short"

## Description

Hello!

I found out "upcoming" bug in `curatedMetagenomicData` (version 3.15.0). This is just upcoming because we have not yet pushed the recent changes to Bioconductor devel; they are currently only available on GitHub.

```
# Install new version of mia
remotes::install_github("microbiome/mia")
package.version("mia")
[1] "1.15.19"

```
In this commit (), we changed the default value of `update.tree` in `agglomerateByRank` to `TRUE`. This means that by default, the tree is pruned and its nodes renamed to match with the agglomerated taxa.

This is causing the issue in `curatedMetagenomicData` when `rownames = "short"`. After agglomeration, the data does not match with phylogeny, and all rows are dropped from the data resulting to dataset with 0 rows.

```
library(curatedMetagenomicData)
library(dplyr)

tse <- sampleMetadata |>
    filter(study_name %in% c(
        "FrankelAE_2017", "GopalakrishnanV_2018", "LeeKA_2022",
        "MatsonV_2018", "PetersBA_2019", "WindTT_2020")) |>
    returnSamples("relative_abundance", rownames = "short")
> tse
class: TreeSummarizedExperiment 
dim: 0 315 
metadata(0):
assays(1): relative_abundance
rownames(0):
rowData names(7): superkingdom phylum ... genus species
colnames(315): frank_P7 frank_P8 ... op176_M1 op177_M1
colData names(140): study_name subject_id ... ALT eGFR
reducedDimNames(0):
mainExpName: NULL
altExpNames(0):
rowLinks: NULL
rowTree: NULL
colLinks: NULL
colTree: NULL
```

This same issue does not happen when `rownames = "long"` as the data is not agglomerated.

The minimal working fix could be to set `agglomerateByRank(..., update.tree = FALSE)`. However, I found out that there might be different number of rows depending on whether `rownames` is `"short"` or `"long"`. This is caused by two reasons:

1. rows without taxonomy information are dropped during agglomeration
2. rows with same taxonomy are agglomerated

First of all, I think that user should get message if rows are removed. Secondly, I think that user expects that the dataset is equal apart from rownames, i.e., the function should not agglomerate the data.

These changes in this PR modifies the function so that:

1. it gives warning if rows are removed due to lacking taxonomy information
2. it does not agglomerate the data but just assigns shorter labels for the rows
```

> tse1 <- sampleMetadata |>
+     filter(study_name %in% c("MatsonV_2018")) |>
+     returnSamples("relative_abundance", rownames = "long")
snapshotDate(): 2024-10-24

$`2021-10-14.MatsonV_2018.relative_abundance`
dropping rows without rowTree matches:
  k__Bacteria|p__Actinobacteria|c__Coriobacteriia|o__Coriobacteriales|f__Coriobacteriaceae|g__Collinsella|s__Collinsella_stercoris
  k__Bacteria|p__Firmicutes|c__Bacilli|o__Lactobacillales|f__Carnobacteriaceae|g__Granulicatella|s__Granulicatella_elegans
  k__Bacteria|p__Proteobacteria|c__Betaproteobacteria|o__Burkholderiales|f__Sutterellaceae|g__Sutterella|s__Sutterella_parvirubra
  k__Bacteria|p__Synergistetes|c__Synergistia|o__Synergistales|f__Synergistaceae|g__Cloacibacillus|s__Cloacibacillus_evryensis

> tse2 <- sampleMetadata |>
+     filter(study_name %in% c("MatsonV_2018")) |>
+     returnSamples("relative_abundance", rownames = "short")
snapshotDate(): 2024-10-24

$`2021-10-14.MatsonV_2018.relative_abundance`
dropping rows without rowTree matches:
  k__Bacteria|p__Actinobacteria|c__Coriobacteriia|o__Coriobacteriales|f__Coriobacteriaceae|g__Collinsella|s__Collinsella_stercoris
  k__Bacteria|p__Firmicutes|c__Bacilli|o__Lactobacillales|f__Carnobacteriaceae|g__Granulicatella|s__Granulicatella_elegans
  k__Bacteria|p__Proteobacteria|c__Betaproteobacteria|o__Burkholderiales|f__Sutterellaceae|g__Sutterella|s__Sutterella_parvirubra
  k__Bacteria|p__Synergistetes|c__Synergistia|o__Synergistales|f__Synergistaceae|g__Cloacibacillus|s__Cloacibacillus_evryensis


$`2021-10-14.MatsonV_2018.relative_abundance`
dropping rows without taxonomy info:
  k__Bacteria|p__Actinobacteria|c__Coriobacteriia|o__Coriobacteriales|f__Coriobacteriaceae|g__Enorma|s__Collinsella_massiliensis

> tse1
class: TreeSummarizedExperiment 
dim: 392 39 
metadata(0):
assays(1): relative_abundance
rownames(392): k__Bacteria|p__Bacteroidetes|c__Bacteroidia|o__Bacteroidales|f__Bacteroidaceae|g__Bacteroides|s__Bacteroides_vulgatus
  k__Bacteria|p__Bacteroidetes|c__Bacteroidia|o__Bacteroidales|f__Rikenellaceae|g__Alistipes|s__Alistipes_putredinis ...
  k__Bacteria|p__Proteobacteria|c__Betaproteobacteria|o__Neisseriales|f__Neisseriaceae|g__Neisseria|s__Neisseria_flavescens
  k__Bacteria|p__Proteobacteria|c__Betaproteobacteria|o__Neisseriales|f__Neisseriaceae|g__Neisseria|s__Neisseria_subflava
rowData names(7): superkingdom phylum ... genus species
colnames(39): SAM_15 SAM_29 ... SAM_19 SAM_17
colData names(140): study_name subject_id ... ALT eGFR
reducedDimNames(0):
mainExpName: NULL
altExpNames(0):
rowLinks: a LinkDataFrame (392 rows)
rowTree: 1 phylo tree(s) (10430 leaves)
colLinks: NULL
colTree: NULL
> tse2
class: TreeSummarizedExperiment 
dim: 391 39 
metadata(0):
assays(1): relative_abundance
rownames(391): species:Phocaeicola vulgatus species:Alistipes putredinis ... species:Neisseria flavescens species:Neisseria subflava
rowData names(7): superkingdom phylum ... genus species
colnames(39): SAM_15 SAM_29 ... SAM_19 SAM_17
colData names(140): study_name subject_id ... ALT eGFR
reducedDimNames(0):
mainExpName: NULL
altExpNames(0):
rowLinks: a LinkDataFrame (391 rows)
rowTree: 1 phylo tree(s) (10430 leaves)
colLinks: NULL
colTree: NULL
```

-Tuomas

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc643a3e9d7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.