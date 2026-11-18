# Issue

**Title:** Release 5.7.0: exact N-origin posterior API

## Description

Release 5.7.0 adds an exact native batch API for the probability that a queried junction codon consists entirely of N additions, conditional on its amino-acid junction and optional V/J calls. It reuses the existing sum-product engine, includes tandem-D histories, excludes P-extended templates, and retains zero-likelihood observations as unsupported nulls. Existing model parameters and Pgen defaults are unchanged.

Validation: all six CI jobs passed for the feature tree, which is identical to dev. The local release tier passed 1,874 tests (7 skipped; 29 deselected); C++ and exact toy-origin tests passed. A clean wheel installation matched all 89 Python files, 268 bundled model files and the native binary, with 11 origin/golden checks passing. Strict documentation builds passed. No scientific matrix recovery or annotation improvement is claimed by this API release.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a216a702d424`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.