# Issue

**Title:** notify user of non-unique

## Description

.
This PR adds a toast message if no groups were found with unique features when coloring the tree using sample metadata/animation. In addition, when coloring the tree using sample metadata, if a category is not represented on the tree then it will be removed from the legend.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8d1a06a1179`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.