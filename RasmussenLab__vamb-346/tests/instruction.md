# Issue

**Title:** WIP: Refactoring of __main__

## Description

I think the invariants are not properly handled sometimes, and also the arguments are not grouped correctly. I'll see if I can make it better.
TODO:
- [x] Move Taxometer to an Options structure
- [x] Move AVAMB to an Options structure, and then also fixup the Snakemake to match
- [x] Remove the Arguments classes
- [x] Go through top-level functions and classes and either simplify their signatures or remove them completely
- [x] Squash, then Merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `761229653605`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.