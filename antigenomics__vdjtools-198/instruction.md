# Issue

**Title:** Release 5.1.0: preserve table PCA explained variance

## Description

Save and restore per-component explained-variance ratios in `TablePCA`, with validation and backward-compatible loading of existing rotations. Document applying separate reference rotations to raw statistical features and retaining unprojected outputs.

Release version: 5.1.0. PCA bundles remain separate outputs and are excluded from package distributions. Focused serialization/projection regressions and previous complete branch CI passed; release-head CI is running.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b945b9bc417`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.