# Issue

**Title:** Read the rep targets of a node as one exchange block in align2clust

## Description

## Problem

`sendRepTargets` flushes at least once per pref partition, so each node reads `512*N` exchange blocks (4,096 on 8 nodes), and `readExchangeRange` gives each block `1/(512*N)` of the buffer. A chunk ends at the first block not read to its end, so the windows become tiny. On Logan-1B with 8 nodes, the nodes aligned in about 6,200 windows and the master in 14,600, which took about 300 s of the 360 s aligning phase.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e8467e0ce5e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.