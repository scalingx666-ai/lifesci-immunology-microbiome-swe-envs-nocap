# Issue

**Title:** Improve getTaxonomyLabels

## Description

Add option to collapse taxonomy ranks and to set lowest rank that will be consider when taxonomy labels are generated.

```
> data(peerj13075)
> tse <- peerj13075
> # Add OTUs to taxonomy table and set taxonomy ranks of mia
> rowData(tse)[["OTU"]] <- rownames(tse)
> setTaxonomyRanks(colnames(rowData(tse)))
> # Get taxonomy labels which correspond to OTUs
> labs <- getTaxonomyLabels(tse)
> labs[62:63]
[1] "OTU184" "OTU185"
> # Get taxonomy labels with genus
> labs <- getTaxonomyLabels(tse, with.rank=TRUE, lowest.rank = "genus")
> labs[62:63]
[1] "genus:Amycolatopsis_OTU184" "genus:Amycolatopsis_OTU185"
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3712080d115`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.