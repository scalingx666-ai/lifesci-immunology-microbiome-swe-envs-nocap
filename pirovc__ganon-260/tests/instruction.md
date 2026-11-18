# Issue

**Title:** ganon version 1.9.0

## Description

- range of `--rel-filter` is now between best and worst match. Before was based only on best match.
- new defaults and fixed cutoff `ganon classify`
- Improved documentation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6700507d90ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.