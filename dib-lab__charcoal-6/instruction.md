# Issue

**Title:** [MRG] pretty viz for tree

## Description

This code uses the R tidytree and ggtree packages to generate a "pretty" visualization of the tree. The tree is constructed from the *json* files, and the visualization is colored by phylum using a small dot placed at the tips. The tree structure that is plotted contains all of the information specified in the *json* files, so we could label the tips with contig name, hashval, etc.

TO DO:
Right now, the visualization is hardcoded to phylum level visualization. This could be improved with a user-specified flag, or all levels could be output, or the first discordant level could be output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84a71a2f792f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.