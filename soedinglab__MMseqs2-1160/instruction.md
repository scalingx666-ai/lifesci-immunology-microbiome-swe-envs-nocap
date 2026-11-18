# Issue

**Title:** Improve align2clust read

## Description

On several nodes, align2clust on `--createdb-mode 3` databases took the gap between the own blocks of a band from the last entry of the band, the shortest one. Logan ends with a few sequences of 2 to 4 residues, so no band fit on 4 nodes and every window read its targets again: the master read 385 GB of a 19 GB database. A merged read adds at most `READ_MERGE_GAP` per block, so a band also fits if that much per block takes at most another eighth of the memory.

Logan subset (127M sequences) on 4 nodes: align2clust 74 s -> 55 s, lin8clust 348 s -> 274 s, at most 25 GB read per node, output byte-identical to 1 node.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8f022a2b7a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.