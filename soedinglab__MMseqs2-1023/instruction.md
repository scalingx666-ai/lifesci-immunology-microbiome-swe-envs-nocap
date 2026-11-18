# Issue

**Title:** cluster with SETalndb is possible

## Description

It's possible to use original seqdb and the alignment db as inputs for `clust`
with --set-mode 1

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8fbdf970d5e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.