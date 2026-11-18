# Issue

**Title:** Make jemalloc optional: allow compiling without it

## Description

There are issues with finding jemalloc in bioconda. So, we generally allow compiling without it.

Also, other fixes for compiling in bioconda for MacOS, like those implemented in: 

Also updated python to 3.12, metagraph-workflows and docker image

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `355eb28cdf6a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.