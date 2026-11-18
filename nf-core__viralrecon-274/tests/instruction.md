# Issue

**Title:** Pre-release bug fixes

## Description

Full-sized tests were failing on Nextflow Tower for both Illumina and ONT. Should be fixed now.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c310ed4bd0f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.