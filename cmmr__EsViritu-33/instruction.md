# Issue

**Title:** Performance improvements

## Description

- parallelize contig stats functions.
- new scheme for assembly clustering.
- changing `pysam.sort()` to `pysam.samtools.sort()` to utilize multiple threads.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbfcf8bc7f71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.