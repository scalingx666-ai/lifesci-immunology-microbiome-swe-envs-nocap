# Issue

**Title:** Add 3D support to `miss_forest_impute`

## Description

Extends `miss_forest_impute` to handle 3D `EHRData` inputs

- Removed `@function_2D_only()` decorator
-  If the input is 3D: flattens the layer to `(n_obs * n_t, n_vars)` (flattening along axis 0) before imputation and reshapes back to `(n_obs, n_vars, n_t)` afterwards using `_apply_over_time_axis`
- Added guard raising `ValueError` when input is 3D but no layer is specified
- Added tests for 3D imputation
- Raising NotImplemented error for unsupported array types (sparse and dask)

Comparison of `miss_forest_impute` and `simple_impute `with mean strategy using physionet2012 dataset with a missingness of 10%: 

```python3
import ehrapy as ep
import ehrdata as ed
import numpy as np

edata_full = ed.dt.physionet2012(layer="tem_data")
edata = edata_full[:200]

full_layer = edata.layers["tem_data"].copy()

rng = np.random.default_rng(42)
non_nan_mask = ~np.isnan(full_layer)
mask_indices = np.where(non_nan_mask)
n_to_mask = int(0.1 * len(mask_indices[0]))
chosen = rng.choice(len(mask_indices[0]), size=n_to_mask, replace=False)

masked_layer = full_layer.copy()
masked_layer[mask_indices[0][chosen], mask_indices[1][chosen], mask_indices[2][chosen]] = np.nan
edata.layers["tem_data"] = masked_layer

edata_mf = edata.copy()
edata_simple = edata.copy()

ep.pp.simple_impute(edata_simple, layer="tem_data", strategy="mean")
ep.pp.miss_forest_impute(edata_mf, layer="tem_data")

true_vals = full_layer[mask_indices[0][chosen], mask_indices[1][chosen], mask_indices[2][chosen]]
mf_vals = edata_mf.layers["tem_data"][mask_indices[0][chosen], mask_indices[1][chosen], mask_indices[2][chosen]]
simple_vals = edata_simple.layers["tem_data"][mask_indices[0][chosen], mask_indices[1][chosen], mask_indices[2][chosen]]

print("True mean:", np.nanmean(true_vals))
print("Miss forest mean:", np.nanmean(mf_vals), "diff:", abs(np.nanmean(mf_vals) - np.nanmean(true_vals)))
print("Simple mean:", np.nanmean(simple_vals), "diff:", abs(np.nanmean(simple_vals) - np.nanmean(true_vals)))

print("True std:", np.nanstd(true_vals))
print("Miss forest std:", np.nanstd(mf_vals), "diff:", abs(np.nanstd(mf_vals) - np.nanstd(true_vals)))
print("Simple std:", np.nanstd(simple_vals), "diff:", abs(np.nanstd(simple_vals) - np.nanstd(true_vals)))

```
Output: 
```
True mean: 70.79201158141458
Miss forest mean: 70.00290934785606 diff: 0.7891022335585234
Simple mean: 71.76743450695217 diff: 0.9754229255375861
True std: 58.31532031908203
Miss forest std: 46.06704701689582 diff: 12.248273302186213
Simple std: 41.852838829183426 diff: 16.462481489898607
```

Note: I used a subset of observations (200) for this evaluation since `miss_forest_impute `got computationally too expensive and crashed (11988 observations × 37 variables × 48 timepoints which after flattening to (n_obs * n_t, n_vars) resulted in a matrix too large for IterativeImputer)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `53f229ea43e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.