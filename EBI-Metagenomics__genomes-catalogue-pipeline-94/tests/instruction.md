# Issue

**Title:** Fix/modify deduplicate script

## Description

- added **folder** input argument (slurm complained `too long input`)
- supports compressed genomes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `50ae466abb13`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.