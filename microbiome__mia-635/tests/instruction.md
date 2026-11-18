# Issue

**Title:** Improve addDivergence

## Description

This PR improves and streamlines the addDivergence() function. Basically, now dissimilarity matrix is calculated first for all sample pairs. From that matrix, the values are assigned to correct sample-pairs. This makes the calculation a lot faster since the dissimilarities are calculated at once for all. The computational cost was an issue especially in miaTime's divergence functions. Moreover, the function now uses getDissimilarity() function which makes the maintenance easier.

This new approach also allows users to specify different reference samples. Previously it was only possible to specify a single reference sample for all samples.

To make the usage simpler, user is advised to store reference sample information to colData (if reference is not "mean" or "median"). However, the function still works with single sample name, vector of samples or vector of numeric values denoting a single sample.

The aim of this all is that now we can utilize this directly from divergence functions from miaTime. I have initialized there a [branch](https://github.com/microbiome/miaTime/tree/bioc_mods), however, I think it is already outdated but might give some idea.

In miaTime functions, we only need to specify the reference samples from previous time points. After this is done, we can call mia::getDivergence().

@Daenarys8 Would you be able to first fix the documentation in this mia::addDivergence() (old description style), check that everything works and then incorporate this function to miaTime divergence functions. You could update miaTime functions before this branch is merged to devel (install mia from this branch). This is to ensure that everything works.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04d0e04a08d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.