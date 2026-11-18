# Issue

**Title:** Updates for seqDist, repGermline and tools.R

## Description

1. seqDist: use V.first/J.first by default
2. repGermline: min_nuc_outside_cdr3 parameter is now public
3. Some frequent operations made generic in tools.R

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `643902184497`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.