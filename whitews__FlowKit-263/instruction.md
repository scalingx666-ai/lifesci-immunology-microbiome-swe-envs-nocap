# Issue

**Title:** add channel_labels check for creating Sample from ndarray

## Description

The docstring of Sample already states that channel_labels are required for passing a numpy ndarray as data, however, there was no actual check if channel_labels was passed. Therefore, I added a quick check and a test, if a ValueError is raised otherwise.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `553eac0675e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.