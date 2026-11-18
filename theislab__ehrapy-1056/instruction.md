# Issue

**Title:** Efficient  non dependency version of MCARTest

## Description

<!-- Many thanks for contributing to this project! -->

**PR Checklist**

<!-- Please fill in the appropriate checklist below (delete whatever is not relevant). These are the most common things requested on pull requests (PRs). -->

- [x] This comment contains a description of changes (with reason)
- [x] Referenced issue is linked
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [ ] Documentation in `docs` is updated

**Description of changes**

-  
- Implemented efficient internal version of MCARTest to remove pyampute dependency
- Benchmark results: ~20x speed up compared to pyampute implementation for Little's test across tested dataset sizes, even larger improvements for pairwise welch t-test (see table below)
- resulting p-values are very close to pyampute results but not identical due to floating point accumulation
- updated tests
- `_little_mcar_test` is a lot of new code, might require additional inline comments for explanation

** Technical Details**
- New `mcar_test` implementation:
  - accepts `EHRData` 2D input (`@function_2D_only()`)
  - rejects sparse matrices
  - materializes dask arrays with a warning (global covariance/pattern grouping requires in-memory data)
- `little` method:
  - computes global means/covariance
  - groups rows by missingness pattern
  - accumulates Little’s chi-square statistic
  - uses `chi2.sf` for p-value
- Numerical robustness:
  - uses `np.linalg.solve`
  - falls back to `np.linalg.pinv` when covariance blocks are singular/ill-conditioned

**Additional context**
 Benchmark results:
#### Method: `little`

| n | p | missing | new (s) | new (MB) | new p | old (s) | old (MB) | old p | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 100 | 10 | 10% | 0.0196 | 0.05 | 0.2394 | 0.3753 | 0.10 | 0.2392 | 19.1x |
| 500 | 20 | 20% | 0.2019 | 0.26 | 0.3134 | 4.0057 | 0.30 | 0.3161 | 19.8x |
| 1000 | 50 | 20% | 0.3283 | 1.28 | 0.4479 | 7.3379 | 1.30 | 0.4487 | 22.4x |
| 2000 | 50 | 30% | 0.6513 | 2.52 | 0.4684 | 14.6964 | 2.53 | 0.4671 | 22.6x |
| 5000 | 50 | 20% | 1.6888 | 6.24 | 0.4981 | 38.0112 | 6.22 | 0.4982 | 22.5x |

#### Method: `ttest`

| n | p | missing | new (s) | new (MB) | new min-p | old (s) | old (MB) | old min-p | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 100 | 10 | 10% | 0.0147 | 0.03 | 0.0054 | 0.6314 | 0.05 | 0.0054 | 43.0x |
| 500 | 20 | 20% | 0.0342 | 0.23 | 0.0062 | 2.5633 | 0.15 | 0.0062 | 75.0x |
| 1000 | 50 | 20% | 0.1252 | 0.86 | 0.0001 | 16.2233 | 0.55 | 0.0001 | 129.6x |
| 2000 | 50 | 30% | 0.2113 | 1.54 | 0.0000 | 15.5949 | 0.95 | 0.0000 | 73.8x |
| 5000 | 50 | 20% | 0.3757 | 3.93 | 0.0002 | 15.6982 | 2.22 | 0.0002 | 41.8x |

<!-- Add any other context or screenshots here. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c696bb08fe5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.