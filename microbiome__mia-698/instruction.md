# Issue

**Title:** Fixes for tree merging and agglomeration

## Description

1. Tree merging

I found out a logical error in the tree merging process. Some phylogenetic trees do not have unique labels, making it impossible to correctly match nodes between trees. For instance, certain trees contain multiple nodes with an empty ("") label, which were previously considered equal which was incorrect.

Now, we only merge trees where all nodes have unique labels. If this requirement is not met, the trees are simply added to the TreeSE object without merging.

2. Agglomeration for multiple trees

Previously, when a TreeSE object contained multiple trees, the tree update during agglomeration did not work correctly.  The function failed both in subsetting and renaming the nodes. This has now been fixed, ensuring that agglomeration works properly even when multiple trees are present.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc6908b3323f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.