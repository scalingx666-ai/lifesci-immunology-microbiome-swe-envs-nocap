# Issue

**Title:** Swap hash

## Description

The main point of this merge is to swap the uint64 kmer encoding with ntHash. There are also a few other changes:

* instead of modulo-N hash in CMS counter placement, use jump hash
* instead of epsilon and delta values for CMS initiation, use a memory limit to set CMS size

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b15ac147d5ef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.