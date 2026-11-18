# Issue

**Title:** Expose gene position coordinates

## Description

* Exposes the start and end location of contig mapping in the output tsvs
* Calculated the positions using the `sbjct_start` and `sbjct_end` fields
* Named these outputs "Hit Start" and "Hit End" but could change to more descriptive names

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2b6789006a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.