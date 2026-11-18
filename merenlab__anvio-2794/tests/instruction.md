# Issue

**Title:** Performance fixies for genome tree calcuations from pangenome graphs

## Description

There are two changes in this PR.

One is a small speed gain, the other is a significant one -- here they are starting with the big change:

Calculating the distance between two genomes to compute a dendrogram from pan-graph was causing extremely long wait times in my 1,300 genome set (it sounds stupid, but actually it was very useful to find some bottlenecks in the code and focus on them). What happened here is the following: we were looping over all genome pairs in the now-replaced code in `anvio/pangenomegraphmanager.py` (i.e., every node and every edge for every pair of genomes to rebuild a `set(edge['genomes'])` object in its most inner loop). Which brought us to the realm of `O(N^3)` complexities. As a result, calculating the dendrogram for my 1,300 genomes took over 5 minutes (which didn't sit well with me). The alternative in this PR below simply vectorizes this step, and produces a bit-identical distance matrix in about 1% of a second for the same set of genomes (yay math).

The other change is a small switch from the poisonous pandas to torturous numpy, which turns a 8-second long process into fractions of a second when large numbers of genomes involved.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa0bd90d54e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.