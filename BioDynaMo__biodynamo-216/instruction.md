# Issue

**Title:** Change BioDynaMo version from vXX.YY-ZZ-gSHA to vXX.YY.ZZ-SHA

## Description

SHA is the git commit hash which can be used to checkout a
specific version with: git checkout SHA

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18d45cd2b8ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.