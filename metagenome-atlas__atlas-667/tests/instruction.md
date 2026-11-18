# Issue

**Title:** Improvement of offline cluster mode

## Description

- these two commits add the download of gunc and dram to local rules which avoids errors on cluster without internet access from jobs
- refers to #666 
- thanks to @Waschina

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `32e1a11af3be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.