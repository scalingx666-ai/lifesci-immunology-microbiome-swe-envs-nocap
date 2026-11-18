# Issue

**Title:** [MRG] replace some of the utils functions with sourmash lca_utils

## Description

Removes `is_lineage_match`, `pop_to_rank`, and `make_lineage` in favor of their versions in sourmash, introduced in  in sourmash v3.4.0.

Fixes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b9c2b8d920f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.