# Issue

**Title:** Add support for named vector for node labels

## Description

Previously, user could only provide linkages between nodes of tree and rows with a vector length of `nrow(x)`. I added support for named vector where names represent `rownames(x)`.

I noticed a problem in `addMDS(x, method = "unifrac")`.

1. It retrieves correct arguments for the MDS calculation, including tree and node labels. These arguments are passed through `scater::calculateMDS()` to `mia::getDissimilarity()`.

2. `scater::calculateMDS()` filters the data (by default, it selects 500 features with highest variance), however, node links are not filtered.

3. This caused an error in `mia::getDissimilarity()` when there were more than 500 node labels.

Now when we use named vector, correct labels can be selected based on filtered abundance table.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `338509d3eec5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.