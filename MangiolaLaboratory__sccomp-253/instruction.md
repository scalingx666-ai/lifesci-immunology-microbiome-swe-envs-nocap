# Issue

**Title:** Enhance sccomp functions with unconstrained predictors

## Description

- Added output for unconstrained predictors in `sccomp_predict` and `sccomp_calculate_residuals`, providing users with direct access to linear scale predictions before softmax transformation.
- Updated documentation to reflect new output columns, including `unconstrained_mean`, `unconstrained_lower`, and `unconstrained_upper`.
- Implemented comprehensive tests to ensure the accuracy and availability of unconstrained predictors in both summary and draws modes.
- Modified Stan model to save linear predictors, ensuring backward compatibility with older models.
- Enhanced user understanding of model behavior through detailed documentation and testing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65d7b4635214`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.