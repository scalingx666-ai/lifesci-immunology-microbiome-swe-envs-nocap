# Issue

**Title:** Support ignoring branch lengths during layout; update tree properties panel UI; some minor clade collapsing changes

## Description

. Also wound up closing #321 (ran into it along the way).

![ignoooore](https://user-images.githubusercontent.com/4177727/91789040-97bab580-ebc2-11ea-89fe-64a600596a77.gif)

The main challenge here was making sure that updating the "ignore lengths?" setting didn't mess with the tree state. This mostly wasn't a problem, but I had to mess around some with how clade collapsing works (since as far as I can tell the previous clade collapsing stuff assumed that clades computed for a given layout could be cached; but here the same layout can have multiple ways of collapsing since the node coordinates vary based on the ignore lengths setting). I believe this works as it should now, but I'm not very familiar with this part of this code.

Other thing we should discuss -- the UI says that "the root node's length is always ignored", but it looks like the unrooted layout uses the root node's length at one point. Since we don't require that the root node has a valid or even specified length, we should discuss this to see what to do.
 
Thanks!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5c74bbbe1d3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.