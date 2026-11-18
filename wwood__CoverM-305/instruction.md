# Issue

**Title:** Add list arguments for reads

## Description

--read1-list, --read2-list, --coupled-list, --interleaved-list and --single-list read inputs

Each takes one or more files listing read paths, one per line (forward and reverse separated by a tab for --coupled-list). Available for genome, contig and make, and can be combined with the direct read arguments.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31147ecd75d3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.