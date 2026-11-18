# Issue

**Title:** Fix: In reclustering, read Vamb clusters with read_clusters

## Description

Previously, reclustering used Pandas' read_csv to read Vamb's clustering file, before splitting each key by underscore to get an integer value of the cluster identity.
Now, use the read_clusters method to read the clusters.

The previous approach was wrong for two reasons:
First, read_csv is too clever, and will, for example, pick an appropriate output type depending on the specific names of the clusters (i.e. clusters named "1" will be parsed as an integer when it's really a string).

Second, we can't rely on clusters being labeled e.g. `vae_1`. The renaming of Vamb clusters to this format was an unecessary hack introduced in the AVAMB pipeline such that the deduplication step could distinguish the source of each cluster. We want cluster names to be able to be arbitrary.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a235e497f482`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.