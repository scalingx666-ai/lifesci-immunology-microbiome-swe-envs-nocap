# Issue

**Title:** Updated folly to fix small vectors, also compilation fixes

## Description

On some systems, it segfaulted when storing annotation rows in folly::SmallVector because of a bug in folly.
Here we update folly to fix that issue.

Also a bunch of other minor changes to make it compile again.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fdd92ce1c4bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.