# Issue

**Title:** Updated pd version for airflow compatibility.

## Description

`airflow` requires a `pandas` version `<1.0.0`, so this PR

* fixes version at `==0.25.3`, and
* reimplements the `diff()` call in `JHU_COVID-19.ipynb` to be backwards compatible with `0.25.3`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b63aa35c804a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.