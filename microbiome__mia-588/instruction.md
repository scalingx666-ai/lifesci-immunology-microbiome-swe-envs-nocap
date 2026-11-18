# Issue

**Title:** Fix tree merging

## Description

1.

mergeSEs did not merge trees, it just added the trees to rowTree slot. If the datasets included multiple trees that did not share taxa, the output included multiple trees. That is not what user expects when the dataset is merged. Now the trees are merged into single tree.

2.

splitOn added hiereachy tree instead of merging the trees when update.tree = TRUE. That is also not what user expects. Now, the trees are combined (or if all taxa is shared between trees, single unchanged tree is outputted).

3.

I also fixed a bug in unsplitOn() function. If the objects being merged did not have names, this lead to an error in rowData merging step.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b1e907fa9ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.