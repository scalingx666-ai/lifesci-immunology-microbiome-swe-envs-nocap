# Issue

**Title:** Remove tagged Singularity files

## Description

and do not pull from Singularity Hub, but build from Docker Hub when using Nextflow with Singularity.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `50678a39d6c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.