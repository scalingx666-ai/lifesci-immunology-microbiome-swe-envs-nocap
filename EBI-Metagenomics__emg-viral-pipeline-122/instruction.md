# Issue

**Title:** remove lsf requirement for ebi profile

## Description

Remove LSF for EBI profile will allow us to run with both ebi,slurm and ebi,lsf options.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5c1ed239731`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.