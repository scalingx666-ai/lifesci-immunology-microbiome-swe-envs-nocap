# Issue

**Title:** Merging Fixes for Alignment Score using Percentile matching of Depth Profiles

## Description

For the alignment score

1. Calculate the depth profile from the bedgraph
2. Find the 97.5 percentile of all depths in all regions
3. Set if/else for 0-depth gaps based on max of 10% of the genome
4. Bin regions based on the jump of 97.5th percentile and the above


The goal is to improve throughput for very large sample sizes as the current implementation does not properly work for high read-count samples.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `17aac436cf90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.