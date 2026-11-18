# Issue

**Title:** Weighted Jaccard

## Description

This pull request consists of count-min sketch-faciliated streaming weighted set comparisons, which works for all supported data structures, including CLI for both sketch and distance.

This should be incorporated into functions determining filenames to which to cache sketches, but this is okay for now.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ae7364853bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.