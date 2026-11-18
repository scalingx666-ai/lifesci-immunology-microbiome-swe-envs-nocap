# Issue

**Title:** Fix `pp.pca` `mask_var` with scanpy 1.13

## Description

Fixes the two `test_scanpy_pp_api.py` failures with scanpy 1.13 ([CI](https://github.com/theislab/ehrapy/actions/runs/43946606695/job/133578132814?pr=1220)).

scanpy 1.13 renamed `mask_var` to `mask`, and the deprecated `mask_var=None` now counts as "not passed", so it falls back to `.var["highly_variable"]` instead of using all variables.

- On scanpy>=1.13, `ep.pp.pca` passes `mask` (column names become `A.var[...]`); scanpy 1.12 is unchanged.
- Removes the test assertion on `uns[...]["params"]["use_highly_variable"]`, which scanpy no longer writes.
- Adds `packaging` as an explicit dependency.

Tested with scanpy 1.13.0 and 1.12.4.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ff528fcaabb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.