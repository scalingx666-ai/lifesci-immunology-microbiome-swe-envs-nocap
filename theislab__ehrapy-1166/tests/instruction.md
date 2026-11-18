# Issue

**Title:** Bump the tutorials to the prediction and refreshed longitudinal tutorials

## Description

Bumps the tutorials submodule to include the new outcome prediction tutorial and the refreshed longitudinal tutorial, and adds the prediction notebook to the docs gallery and to the notebook CI, which now installs the `ml` extra.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31b2b6020f1e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.