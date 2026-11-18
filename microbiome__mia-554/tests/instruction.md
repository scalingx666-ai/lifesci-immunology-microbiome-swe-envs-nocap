# Issue

**Title:** Integrate agglomerateBy* functions

## Description

agglomerateByRank() uses agglomerateByVariable() internally. However, for instance tree agglomeration was done separately in *Rank function, and *Rank and *Variable used different methods to agglomerate trees.

--> Take into account this. Do all the agglomeration steps in *Variable function, and leave only rank-specific functionality in *Rank function.

Moreover, *Variable() function's tree agglomeration method did not take into account the problem described here  It used node numbers instead of labels, but when TreeSE is created nodes are matched with rows/cols based on the label. This means that label found in row/colLinks matches with the tree (no need to make things more complex with node numbers).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e1bbf5aa16b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.