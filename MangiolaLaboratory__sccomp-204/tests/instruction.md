# Issue

**Title:** Update `prepare_replicate_data` to use `original_formula_composition`…

## Description

… for grouping names

- Modified the `prepare_replicate_data` function to accept `original_formula_composition` as a parameter.
- Updated the calculation of `original_grouping_names` to utilize `original_formula_composition` instead of `formula_composition`.
- Enhanced the `replicate_data` function to pass the original formula composition from the data attributes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d8b27b73341`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.