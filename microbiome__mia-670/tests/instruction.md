# Issue

**Title:** Utilize vegan::rrarefy

## Description

Utilize `vegan::rrarefy` when `replace=FALSE`. Utilize own internal function (inspared by `phyloseq::rarefy_even_depth`) when `replace=TRUE`.

Related to

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d2f40dc9c7f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.