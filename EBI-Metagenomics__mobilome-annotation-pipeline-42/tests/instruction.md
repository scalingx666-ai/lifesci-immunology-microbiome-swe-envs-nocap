# Issue

**Title:** Bugfix/output directories

## Description

Some minor modifications to output directory.

- genomad_out was a nested directory
- ice finder tmp takes up a lot of space and not needed. This is the best solution I could find.. happy if you find a better one!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `109ba0fdbb60`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.