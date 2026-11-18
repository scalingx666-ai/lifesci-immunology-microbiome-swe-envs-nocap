# Issue

**Title:** [BUG] fixes clade collapse bug

## Description

This fixes a bug that occurs when a clade with a single tip is collapsed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b53a17da8da3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.