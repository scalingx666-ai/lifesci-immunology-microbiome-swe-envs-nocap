# Issue

**Title:** Update rootstock on 2022-03-08

## Description

I noticed a huge number of DOI citation warnings in recent builds.  These are due to changes in the external services that Manubot uses for DOI metadata.  Updating Manubot should reduce these warnings.

We'll also gain the ability to build the manuscript on demand from https://github.com/greenelab/covid19-review/actions without creating a commit or pull request.

This updates the build script so we should carefully check the build log and outputs before merging.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `823fe18cdb1c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.