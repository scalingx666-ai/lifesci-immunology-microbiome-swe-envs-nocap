# Issue

**Title:** add more summary output columns and rearrange the columns to be more useful

## Description

add `f_ident`, `f_removed`, and `provided_lineage`.

also provides numbers and lineages for early-exit situations, even if no decontamination has happened.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f71fefb2926a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.