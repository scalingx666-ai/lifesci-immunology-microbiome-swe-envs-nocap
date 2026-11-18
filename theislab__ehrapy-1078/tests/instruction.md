# Issue

**Title:** feat: 3D & lazy dask array support for ep.pp.encode

## Description

.

`ep.pp.encode` now accepts dask arrays and 3D longitudinal layers.

- **Dask:** Three internal array-assembly helpers (`_delete_columns`, `_prepend_columns`, `_append_columns`) are now `@singledispatch` with `np.ndarray` and `DaskArray` registrations, matching the pattern in `_normalization.py`, `_missing_data.py`, and `_imputation.py`. The dask path uses `da.concatenate` and lazy fancy indexing, so `.X` and `layers["original"]` stay lazy dask arrays end-to-end.
- **3D longitudinal:** `encode` dispatches on `X.ndim`. The 3D path reshapes `(n_obs, n_vars, n_time)` → `(n_obs·n_time, n_vars)` in patient-major order, runs the existing 2D pipeline on a temporary `EHRData` with obs repeated per timepoint, then reshapes the encoded result and the `original` layer back to 3D. The encoder fits on values stacked across time so the category space is shared across timepoints. `obs` stores the first-timepoint value of each encoded categorical. Re-encoding a previously-encoded 3D `EHRData` raises `NotImplementedError` (per-timepoint variation is not preserved after the first encoding).
- **Tests:** parametrized the main encode tests and the three quality_control tests that use encode over `ARRAY_TYPES_NONNUMERIC`. Added two 3D-specific tests for the longitudinal path.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3db4558e5c5b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.