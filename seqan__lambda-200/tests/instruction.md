# Issue

**Title:** [feature] compressed indexes

## Description

@sarahet Can you give this a try with a run on a big database? Just a single run should already be helpful.

Also, it would be great to see the filesizes of the compressed VS uncompressed index. For Uniprot, it is roughly 50%.

If also possible, can you check the CPU-Usage during saving and loading the index? It is quite difficult for me to measure on small databases...

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `63e75960835e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.