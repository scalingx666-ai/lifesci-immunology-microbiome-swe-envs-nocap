# Issue

**Title:** Fix request gpu

## Description

- [x] Test gpu submission

Note that gpu envs need to be built with access to the relevant gpus (e.g. on gpu interactive job)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `177fcd095965`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.