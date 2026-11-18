# Issue

**Title:** Build succinct graphs in place by default; --in-ram for building in RAM

## Description

- Now succinct graphs are constructed in place by default.
- Deprecated flag `--inplace`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bfb20c487286`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.