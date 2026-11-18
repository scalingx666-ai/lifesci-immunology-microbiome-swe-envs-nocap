# Issue

**Title:** BLD: Drop support for Python 2.7

## Description

:snake: 🔥 

We need to continue to use gjslint which only runs in 2.7.x (hence the invocation in .travis.yml) but otherwise we should be good.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4775bf9acc0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.