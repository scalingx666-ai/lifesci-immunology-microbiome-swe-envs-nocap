# Issue

**Title:** updated sdsl-lite: removed memory overhead in select_support_mcl loaded with mmap

## Description

Significantly reduces the RAM usage for select_support_mcl (and many other data structures using it) loaded with mmap

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `352084443ab6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.