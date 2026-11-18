# Issue

**Title:** remove nonsimp_update.formula

## Description

stacked on #825



Eliminates remaining uses of `nonsimp_update.formula` (and `append_rhs.formula`), avoiding potential issues that can arise with environments when these functions are used to manipulate formulas.

Depends on `master` versions of `ergm`, `ergm.ego`, and `tergm`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a80d2d7a2226`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.