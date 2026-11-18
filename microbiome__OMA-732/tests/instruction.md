# Issue

**Title:** Relevant packages

## Description

Related to these issues:  & 

OMA already cited MicrobiotaProcess, but this PR adds citation also for microeco.

These both packages implement unique framework for microbiome analysis. They introduce own classed for storing microbiome data and importers for TreeSE. Even though they are great packages, I think mentioning them in the list is enough. As they introduce their own data containers, they are not part of the SummarizedExperiment ecosystem, which is the main point of OMA.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f82723051971`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.