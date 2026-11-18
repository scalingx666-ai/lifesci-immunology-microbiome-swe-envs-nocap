# Issue

**Title:** Add 3D support for knn_impute

## Description

`ep.pp.knn_impute()` is extended to support 3D EHRdata.

**Description of changes**

- Updated _knn_impute to handle 3D array by first flattening it along the axis 0 and then passing it to the imputer 
- Added test for 3D numerical imputation using the existing edata_mini_3D_missing_values fixture

**Technical details**
For 3D array with shape n_obs, n_var, n_t:

1. The array is sliced to the requested variable and reshaped to (n_obs * n_t, n_var), each patient-timepoint becomes a row
2. The existing complete column logic runs on the flattened 2D array
3. After imputation the result is reshaped back to (n_obs, n_t, n_var) and transposed to (n_obs, n_var, n_t), then written back to only the requested variable positions in the layer

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb94a43dcab0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.