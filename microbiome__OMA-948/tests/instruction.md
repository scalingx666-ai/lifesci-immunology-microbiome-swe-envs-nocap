# Issue

**Title:** Filter Joint-RPCA input with base R

## Description

Replaces `mia::filterRPCAInput()` in the Joint-RPCA chapter with explicit stepwise filtering in base R, in the same order as gemelli (the original Python implementation of Joint-RPCA):

```r
# Filter the raw counts in steps
tse <- mae[["microbiota"]]
# 1. Remove genera with 10 reads or fewer in total
tse <- tse[rowSums(assay(tse, "counts")) > 10, ]
# 2. Remove genera that are present in 10% or less of the samples
tse <- tse[rowMeans(assay(tse, "counts") > 0) > 0.1, ]
# 3. Remove samples with 1000 reads or fewer
tse <- tse[, colSums(assay(tse, "counts")) > 1000]
mae[["microbiota"]] <- tse
```

Each step is computed from the data left by the previous step, so, for example, library sizes are calculated after the rare genera are removed. `filterRPCAInput()` computes all metrics from the unfiltered object (see microbiome/mia#888, where it is proposed for deprecation).

Effect on HintikkaXOData (genus level, 262 genera, 40 samples): step 1 keeps 145 genera, step 2 keeps 142, and step 3 removes no samples (the smallest library size is 30,744). Previously the chapter filtered by prevalence only and kept 145 genera. The chapter's text makes no claims that depend on the exact genera; the Joint-RPCA code was run end to end with the new input.

`filterRPCAInput()` is also removed from the exercise's list of useful functions.

A general `subsetBy()` for this kind of stepwise filtering is proposed in microbiome/mia#894; the chapter can switch to it once it is available.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af357ad6291f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.