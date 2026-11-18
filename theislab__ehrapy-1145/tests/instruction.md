# Issue

**Title:** Store rank_features_groups results only for the compared groups

## Description

`ep.tl.rank_features_groups` now stores results only for the compared groups, like `sc.tl.rank_genes_groups`, instead of also for the `reference` and for groups outside `groups`. This removes the empty "reference vs. reference" panel in `ep.pl.rank_features_groups` and the crash on categorical features with a `groups` subset.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55c5f0bfb718`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.