# Issue

**Title:** FIX bug in github actions // ENH update models to avoid scikit-learn version conflict

## Description

Minor changes:

- Removed the deprecated flag '--features=in-tree-build' in the pip install command to avoid errors
  when setting up the environment

- Updated the version used in the GitHub Actions to v3 to avoid NodeJS conflicts with new CPUs
  GitHub use

- Updated models for AMP and Hemolytic peptide predictions, yet trained with the same data,
  but using a newer distribution of scikit-learn (v.1.1.2) to avoid warning messages and/or prediction
  inconsistencies. -- Results should be consistent with previous versions

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01fb91e528b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.