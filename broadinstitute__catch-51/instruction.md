# Issue

**Title:** Add heuristic to decide which clustering method to use

## Description

The comment added by this commit to `probe_designer` details a problem with the recently-introduced default method for clustering input sequences (`simple`; see d6ef14e). The problem occurs on long genomes (e.g., bacterial) when also breaking the genomes into fragments and clustering those.

This commit introduces a crude heuristic to select whether to use the newer `simple` method (which finds connected components) or the older, most resource-intensive `hierarchical` method (which uses agglomerative hierarchical clustering). `hierarchical` avoids the problem.

The argument `--cluster-and-design-separately-method` now has a new choice, `choose`, to use the heuristic to decide the method, and `choose` is the default setting for that argument.

This change will likely improve performance with out-of-the-box usage (e.g., running `design_large.py`) on long genomes, including bacterial genomes, following d6ef14e, which made `simple` be the default clustering method.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eb6713dfd8a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.