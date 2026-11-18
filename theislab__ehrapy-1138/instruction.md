# Issue

**Title:** Bump ehrdata and tutorials submodules

## Description

Moves ehrdata to main with the 3D `infer_feature_types` fix (theislab/ehrdata#311), and the tutorials to the versions that keep longitudinal data in `.X` (theislab/ehrapy-tutorials#69) and explain feature types and encodings (theislab/ehrapy-tutorials#68).
The notebook CI then runs the updated tutorials against ehrapy main.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dbb3b7858017`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.