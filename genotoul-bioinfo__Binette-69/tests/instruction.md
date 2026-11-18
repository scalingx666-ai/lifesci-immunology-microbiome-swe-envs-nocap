# Issue

**Title:** Speed Up Binette Startup Time

## Description

Binette had slow startup (>2 seconds) because of CheckM2 and Keras/TensorFlow imports.

This PR adds a lazy loading to only import heavy dependencies when actually needed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98a732ba9bc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.