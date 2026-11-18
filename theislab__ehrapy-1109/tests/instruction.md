# Issue

**Title:** ep.pp.knn_impute clean behaviour with different array types

## Description

**Description of changes**

Adapts `knn_impute `to follow the same array-type dispatch pattern already used by `simple_impute` and `miss_forest_impute`. The core matrix processing logic (2D/3D reshaping, anchor-column selection, and the call to the imputer's `fit_transform`) is now extracted into a singledispatch function`, _knn_impute_function`, registered for `np.ndarray`. Any other array type (dask arrays, scipy sparse arrays) now raises a clear NotImplementedError. 

**Technical details**
Neither of the two backends knn_impute supports (sklearn.impute.KNNImputer, fknni.FastKNNImputer) can operate on sparse or dask input. Thats why, it is now restricted to `np.ndarray`

Added `test_knn_impute_array_types `in `tests/preprocessing/test_imputation.py`, parametrized over `ARRAY_TYPES_NUMERIC `and both knn_impute backends (scikit-learn, faiss), asserting NotImplementedError for dask/sparse input and correct imputation for np.ndarray.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e92f2ca9da46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.