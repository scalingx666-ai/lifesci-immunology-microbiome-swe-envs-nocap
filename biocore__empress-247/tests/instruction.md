# Issue

**Title:** Remove empty samples / features in the table after matching but before shearing

## Description

Ensures that empty features in the table are removed from the tree if shearing is requested (could impact datasets where the user rarefied a table and this resulted in certain features having abundances of 0). Also gives a fancy error if these "empty" samples or features are present in the ordination (should probably never happen in practice, but if it does happen then the user'll know at least).

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b2958241d8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.