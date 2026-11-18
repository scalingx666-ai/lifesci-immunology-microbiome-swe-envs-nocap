# Issue

**Title:** traceback on error

## Description

*WIP*

- write traceback to stdout if `control$traceback.on.error` (default false)
- dump `dat` on error if `control$dump.dat.on.error`

this would simplify the debugging on HPC, specifically for stochastic bugs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56c30163f053`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.