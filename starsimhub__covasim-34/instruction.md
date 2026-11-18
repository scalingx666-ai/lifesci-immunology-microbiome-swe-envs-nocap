# Issue

**Title:** Reduce Docker image size by switching to miniconda base image

## Description

.

Bring the image size down from ~3.12GB to ~1.83GB.
Explicitly install the `gcc` supplied by conda and ensure it is available to the shell when building Python package dependencies. (If this looks too messy, I'm happy to switch to the `python:3` image instead, which gives us a ~1.96GB image without the need to tweak the environment to get `gcc`.)

Based on #32 to avoid conflicts. Only the last two commits are new. This should be merged only after that PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec217b6d7c46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.