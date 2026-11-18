# Issue

**Title:** Bound sample PCA application memory and thread use

## Description

Sample PCA application converted and copied the full feature table before projection. Wide cohort tables therefore incurred additional memory proportional to all samples and features.

Project byte-bounded row blocks into one preallocated score matrix, preserve feature-space checks and metadata, and scope BLAS limits with the existing numerical phase helper. Add `project-features --threads` for fitting and application; avoid a redundant dense copy during fitting.

Validation: 52 focused projection/configured-fit checks passed; the final failure-cleanup regression also passed (10 projection checks). Strict Sphinx build and Ruff passed. The regression checks bounded conversion, dense-oracle agreement, missing values, input preservation, invalid budgets, and thread restoration after success and failure.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55ccf1ad1813`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.