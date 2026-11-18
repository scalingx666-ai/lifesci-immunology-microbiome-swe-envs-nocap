# Issue

**Title:** 135 minhash reduction cross species not working

## Description

- Added automated weighting based on sample type
- Color coordinated z score for low priority, standard abundance organisms for clinical samples
- Added plasmid weight comparisons for more granular strain reporting
- Adding some background args to speed up benchmarking
- Altered some usage docs for parameters

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0c0533bb526`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.