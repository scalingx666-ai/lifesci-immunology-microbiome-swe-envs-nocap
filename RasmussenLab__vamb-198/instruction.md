# Issue

**Title:** Rehaul and tweak clustering

## Description

This commit is a squashed version of several commits that can be found on the exp_cluster branch, and which has been tested individually. It contains the following changes:

Seed ordering

Before, the order in which seed contigs were picked was randomized, in order to prevent bias arising from the order of the sequences in the FASTA files. Now, we pick the seeds in a precomputed order, here the contig length. The idea is that the contigs which we are most confident should belong to a good cluster gets "first pick" during clustering to see if they can form proper clusters.

Length weighting

When computing the distance histogram from which the threshold is found, contigs are now weighed by their length. This should make it more likely to correctly detect clusters composed of a small number of large contigs. In testing, this improves binning result, and the distance histograms become clearer and more well-shaped.

Simplified medoid search

Before, the medoid should have the lowest mean distance to each contig within a small radius. Now, since we take length into accounts when finding the threshold, instead choose the medoid that has the highest "local density". This is computed as sum(length * (R - distance)) where R is a small contant, for each contig where distance <= R.
Also, the random sampling of medoids is now simpler and should be more efficient

Various refactorings and tweaks

* Update the hyperparameters windowsize and minsuccesses to make Vamb the cluster selection criteria stricter
* Implement a pack function which deleted used points in the matrix and associated vectors. This enables better control of when the matrix is packed, which should make clustering faster
* When the peak valley ratio is raised, start over from the highest ordered seed. This makes sure the highest ordered seeds are attempted multiple times.
* Misc refactoring

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9cfb09805490`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.