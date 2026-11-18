# Issue

**Title:** Add possibility to echo version

## Description

Hi!
For each of the scripts (bracken, bracken-build and install-bracken) -v can be used to echo the version and exit. This is quite important, and an open issue #118

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88b77381684e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.