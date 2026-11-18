# Issue

**Title:** filter genomes with provided info before CheckM

## Description

I ran into a stumbling block when trying to run dRep on a large dataset. While most of the bins had CheckM statistics available from DAS_Tool, a minority were missing (see this issue: ). 

I figured it would be nice to let drep crossreference the genomeInfo table with the genome input table and only run CheckM on those genomes missing form genomeInfo, rather than erroring out if any are missing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a82f894a58f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.