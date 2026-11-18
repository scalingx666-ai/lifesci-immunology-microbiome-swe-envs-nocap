# Issue

**Title:** Add --compress CLI flag to compress FASTA bins

## Description

This cuts down on disk space by about 3x for very little cost. Also fix up some type annotations. That should probably have been a different commit but oh well.

Supersedes #457
Thank you for the suggestion, @linsalrob

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b3c134067d0a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.