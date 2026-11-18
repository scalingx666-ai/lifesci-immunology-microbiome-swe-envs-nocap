# Issue

**Title:** 3D support for `mice_forest_impute`

## Description

Extends `mice_forest_impute` to handle 3D inputs, following the same flatten/unflatten pattern established for `knn_impute`

- Raising ValueError when input is 3D but no layer is specified
- Added 3D support: flattening the layer to `(n_obs * n_t, n_vars)` before building the DataFrame and reshapes back to `(n_obs, n_vars, n_t)` after imputation
- Added tests for 3D 

*Technical notes*

The 3D path is asymmetric with the 2D:
- 2D: keeps the full matrix, uses `column_indices = var_indices` to select columns to impute, writes back the full DataFrame
- 3D: pre slices to `var_indices` before flattening, uses `column_indices = list(range(len(var_indices)))`, writes back only to `var_indices` positions

This is necessary for two reasons I observed when trying to making it symmetric:
1. Flattening the full 3D matrix with `.astype()` crashes on categorical columns (object dtype arrays with string values were not able to be cast to float)
2. Without explicit float casting, object dtype arrays cause NaN predictions in miceforest's internal KD-tree, raising `ValueError: 'x' must be finite`

Comparison of `mice_forest_impute `and `simple_impute `with mean strategy using physionet2012 dataset with a missingness of 10%:

```python3
import ehrapy as ep
import ehrdata as ed
import numpy as np

edata_full = ed.dt.physionet2012(layer="tem_data")
ed.infer_feature_types(edata_full, layer="tem_data")
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
ep.pp.mice_forest_impute(edata_mf, layer="tem_data")

true_vals = full_layer[mask_indices[0][chosen], mask_indices[1][chosen], mask_indices[2][chosen]]
mf_vals = edata_mf.layers["tem_data"][mask_indices[0][chosen], mask_indices[1][chosen], mask_indices[2][chosen]]
simple_vals = edata_simple.layers["tem_data"][mask_indices[0][chosen], mask_indices[1][chosen], mask_indices[2][chosen]]

print("True mean:", np.nanmean(true_vals))
print("Mice forest mean:", np.nanmean(mf_vals), "diff:", abs(np.nanmean(mf_vals) - np.nanmean(true_vals)))
print("Simple mean:", np.nanmean(simple_vals), "diff:", abs(np.nanmean(simple_vals) - np.nanmean(true_vals)))

print("True std:", np.nanstd(true_vals))
print("Mice forest std:", np.nanstd(mf_vals), "diff:", abs(np.nanstd(mf_vals) - np.nanstd(true_vals)))
print("Simple std:", np.nanstd(simple_vals), "diff:", abs(np.nanstd(simple_vals) - np.nanstd(true_vals)))
```

Output:
 
```
True mean: 70.79201158141458
Mice forest mean: 71.61526264993796 diff: 0.8232510685233763
Simple mean: 71.76743450695217 diff: 0.9754229255375861
True std: 58.31532031908203
Mice forest std: 61.67046958546801 diff: 3.355149266385979
Simple std: 41.852838829183426 diff: 16.462481489898607
```

Note: I used a subset of observations (200) for this evaluation since mice_forest_impute got computationally too expensive (11988 observations × 37 variables × 48 timepoints which after flattening to (n_obs * n_t, n_vars))

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c153915b327`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.