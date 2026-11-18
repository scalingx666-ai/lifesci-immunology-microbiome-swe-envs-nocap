# Issue

**Title:** ENH:Allow for missing features in feature metadata

## Description

Allows for feature metadata to not include some of the features
represented in the ordination. The errors and warnings have been updated
to properly refer to either features or samples. I've added a couple of
tests to validate the error/warning messages.

  and #733

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c63e8be156bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.