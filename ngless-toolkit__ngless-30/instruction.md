# Issue

**Title:** Fix issues with building and testing a static binary

## Description

Also provide a gitlab testing file which will allow us to use the gitlab infrastructure to have an additional docker based test layer and automatically build a usable static binary.

The idea is to have https://gitlab.com/ngless/ngless/ which simply clones from github and builds.
All activity is still centered on github.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5059d9e66ec9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.