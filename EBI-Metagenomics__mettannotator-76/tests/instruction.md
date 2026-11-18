# Issue

**Title:** Fix/docs

## Description

Minor changes to the README - mettannotator produces header-only files if there are no annotations detected by a specific tool; documentation now clarifies use cases for running slow tools on an incomplete fast-run folder.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `502fd1e7c6c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.