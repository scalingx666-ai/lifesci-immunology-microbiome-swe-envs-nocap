# Issue

**Title:** Fix documentation errors and warnings by suppressing verbose output

## Description

This PR addresses issues where documentation generation produced verbose error logs from AutoTS and deprecation warnings from the pca package.

Changes:
- Modified `covsirphy/science/_autots.py` to redirect stdout and stderr to `os.devnull` during `AutoTS.fit()` when `verbose` is 0 or less. This suppresses "Template Eval Error" messages that clutter output.
- Updated `covsirphy/science/ode_scenario.py` to change the default `verbose` level in `predict()` from 1 to 0, ensuring cleaner default output.
- Updated `covsirphy/science/ml.py` to map `config.logger_level` (integer) to the corresponding string (e.g., "info") expected by the `pca` package, resolving a deprecation warning.
- Ensured the `verbose` argument is correctly propagated from `ODEScenario.predict` to `MLEngineer` and `_AutoTSHandler`.

---
*PR created automatically by Jules for task [17032068379422926603](https://jules.google.com/task/17032068379422926603) started by @lisphilar*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66af02583cde`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.