# Issue

**Title:** Fix `ep.pp.mcar_test(method="little")` covariance estimation

## Description

`_little_mcar_test` estimated the pairwise-deletion covariance matrix incorrectly: it centered each covariance entry using each column's global mean (computed from all of that column's non-missing values across the whole dataset), instead of the pairwise mean (recomputed per variable pair, using only the rows where both variables in that pair are observed).

### Fix

`cov_global` in `_little_mcar_test` (`ehrapy/preprocessing/_quality_control.py`) is now computed as a true pairwise-deletion covariance matrix:

- For each pair `(i, j)`, the sum-of-products `S[i,j]` and the pairwise means are computed only over rows where both `i` and `j` are observed
- This mirrors `pandas.DataFrame.cov()`'s pairwise behavior, using vectorized matrix operations 


**Example:** 

```python
import ehrdata as ed
import ehrapy as ep

edata = ed.dt.ehrdata_blobs(
    n_observations=900, n_variables=50, missing_values=0.5, random_state=7,
    n_centers=1, cluster_std=1.0, base_timepoints=1,
)
ep.pp.mcar_test(edata, method="little")

```

**Output:** 
```
Before: 0.19634452095098048
After: 0.20943902578032475
pyampute reference: 0.20943902578030515 (matches to float precision)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee0ca8253c11`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.