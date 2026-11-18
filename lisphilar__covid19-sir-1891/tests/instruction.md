# Issue

**Title:** Bump AutoTS to 1.0.0 and fix import error

## Description

This PR updates the `AutoTS` dependency to version 1.0.0.

Changes:
- Updated `pyproject.toml` to use `AutoTS = "^1.0.0"`.
- Updated `poetry.lock`.
- Fixed `ImportError` in `covsirphy/science/_autots.py`. `fake_regressor` was moved to `autots.tools.regressor` in AutoTS 1.0.0.

Verified that all tests pass. Confirmed that no removed models (ComponentAnalysis, TFPRegression, TensorflowSTS, Greykite, NeuralProphet, UnivariateRegression) are explicitly used in the codebase.

---
*PR created automatically by Jules for task [12270134746761733281](https://jules.google.com/task/12270134746761733281) started by @lisphilar*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a8f343df4b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.