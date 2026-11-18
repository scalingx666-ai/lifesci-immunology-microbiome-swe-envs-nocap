# Issue

**Title:** Dev

## Description

- removes ssao, *critical*
- appends singletons reads to sam. 
- adds unmapped reads to sam file. -> statistics of pileup and assembly report are right.

mapped reads are calculated as: 

(mapped singletons + 2 x mapped pe) / (QC singletons + 2* QC paired end reads)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa1f64d64c13`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.