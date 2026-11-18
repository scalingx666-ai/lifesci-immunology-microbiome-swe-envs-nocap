# Issue

**Title:** Mirror scanpy's image-comparison tolerances to fix CPU plotting test failures

## Description

## Mirror scanpy's image-comparison tolerances to fix CPU plotting test failures



CPU test suite (`hatch-test.py3.12`, `hatch-test.py3.14`) was failing on
image-comparison plotting tests with `AssertionError`. The comparisons go through check_same_image in `tests/conftest.py`, which wraps
`matplotlib.testing.compare.compare_images(expected, actual, tol=tol)` The `tol` is an RMS pixel difference on a 0–255 scale. ehrapy was setting it far too strictly (`1e-1`–`2e-1` ≈ near pixel-perfect), whereas scanpy uses the same mechanism with `tol` of 5–40 (most commonly 15). matplotlib is pinned and resolves transitively to 3.10.5; small rendering differences across environments blow past the tiny threshold even when plots are visually equivalent.

### What this PR does
Mirrors scanpy's tolerance approach for the **tolerance-solvable** failures (30
tests):
- temporary mirror of matplotlib in the scanpy dependency list (pyproject.toml): once released scanpy carries the exclusion, it can be removed
- `tests/conftest.py`: `check_same_image` now defaults to `tol=15` (scanpy's
  most common value); individual tests bump it only where rendering legitimately
  differs more.
- Per-test tolerances assigned in clean tiers (each ≥1.3× the observed RMS):

  | tier | used for |
  |---|---|
  | **15** (default) | sankey, cohort flowchart, scanpy scatter/violin/clustermap/pca/pca_overview |
  | **25** | missingno (all), scanpy heatmap/dotplot/tracks/matrix/stacked_violin/rank_heatmap/rank_dotplot/pca_variance |
  | **35** | cohort barplots, scanpy dpt_timeseries |
  | **40** | scanpy pca_loadings (highest RMS, 30.8) |

- **Sensitivity tests keep their tight `tol=1e-1`** (e.g.
  `test_CohortTracker_plot_cohort_barplot_test_sensitivity`,
  `test_CohortTracker_flowchart_image_sensitivity`) so they still detect
  intentional differences — the tiers were chosen to remain meaningful, not so
  loose they defeat the comparison.

Two failures are **not** tolerance-fixable:
- `test_catplot_vanilla`, `test_stratified_table_one_plot` — image **size**
  mismatch (tolerance-independent; `compare_images` bails before computing RMS) -> pinned matplotlib 

Reference code on scanpy repo for image comparison tolerance: https://github.com/scverse/scanpy/blob/ee7707bc208132cca8387e542d0532f6967f68cc/tests/test_plotting.py#L567

Reference on scanpy pyproject.toml for pinning matplotlib: https://github.com/scverse/scanpy/blob/d5a745e1258f5ca6a23c6a790f27b40d7ad05418/pyproject.toml#L60

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eaa0d8b4b1fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.