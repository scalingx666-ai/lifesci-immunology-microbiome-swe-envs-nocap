# Issue

**Title:** Support UniFrac and pre-calculated dissimilarity in getPERMANOVA

## Description

. Extends `getPERMANOVA` and `addPERMANOVA` to support UniFrac and pre-calculated dissimilarity matrices. Tree-aware metrics (`unifrac`, `overlap`, `jsd`) are computed via `mia::getDissimilarity()`, and pre-calculated matrices can be retrieved via `dis.name` from `metadata(x)` or passed directly as `dist` objects. Also updates dispersion testing in `.calculate_homogeneity()` to accept distance objects directly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e425d954c1de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.