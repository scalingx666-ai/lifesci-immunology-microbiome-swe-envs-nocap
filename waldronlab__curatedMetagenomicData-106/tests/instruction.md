# Issue

**Title:** more performant databases

## Description

I converted the pipeline to read from public copies of uniref and chocophlan stored in google cloud storage. The download speeds are 10x what we get from the humann2 website and will scale. The databases are no longer "configurable", but the docker image can be updated if needed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c5ee83c1049`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.