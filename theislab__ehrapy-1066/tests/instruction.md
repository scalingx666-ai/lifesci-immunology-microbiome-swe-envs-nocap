# Issue

**Title:** feat: add stratified Table One for baseline comparisons

## Description

Fixes 

## Summary

- Add `ep.tl.stratified_table_one(edata, groupby=...)` to build a publication-ready, stratified Table 1 over `edata.obs`. Per-variable tests are selected automatically (chi-square / Fisher's exact for categoricals, t-test / ANOVA for normal continuous, Mann-Whitney U / Kruskal-Wallis for variables in `nonnormal`), with optional multiple-testing correction via `pval_adjust`. Wraps the `tableone` package; categorical type is auto-detected via `ed.infer_feature_types`. Results (rendered DataFrame + parsed intermediates) land in `edata.uns[key_added]`.
- Add `ep.pl.stratified_table_one(edata)` companion plot: a HoloViews `Layout` with one panel per variable (stacked bars for categoricals, per-group bars for continuous) and per-variable p-values in the panel titles.

- Fix a long-standing test-order fragility: `tests/plot/test_scanpy_pl_api.py` was calling `plt.style.use("default")` at module-import time, leaking matplotlib state into every test in the suite. That call now lives in a single autouse fixture in `tests/conftest.py` that snapshots and restores `rcParams` around every test, so image-comparison tests behave deterministically regardless of collection order.

## Minimal example

```python
import ehrapy as ep
import ehrdata as ed

edata = ed.dt.diabetes_130_fairlearn(
    columns_obs_only=["gender", "race", "age", "readmit_binary", "num_procedures"]
)

ep.tl.stratified_table_one(
    edata,
    groupby="readmit_binary",
    columns=["gender", "race", "age", "num_procedures"],
    nonnormal=["num_procedures"],
)

# The rendered Table 1 (pandas DataFrame) — export with .to_csv / .to_latex / .to_markdown
edata.uns["stratified_table_one"]["table"]

# Companion plot
ep.pl.stratified_table_one(edata)
```

Example output for the small `dataset1.csv` fixture used in tests (`groupby="station"`, `nonnormal=["glucose"]`):

```
                          Grouped by station
                                     Missing             Overall               ICU                 MICU P-Value
n                                                             12                 6                    6
glucose, median [Q1,Q3]                    0  107.5 [83.8,125.0]  82.5 [80.0,88.8]  125.0 [121.2,125.0]   0.053
weight, mean (SD)                          0         76.0 (14.9)       81.7 (14.7)          70.3 (14.0)   0.201
disease, n (%)          A                               4 (33.3)          2 (33.3)             2 (33.3)   1.000
                        B                               4 (33.3)          2 (33.3)             2 (33.3)
                        C                               4 (33.3)          2 (33.3)             2 (33.3)
```

## Plot preview

![stratified_table_one preview](https://raw.githubusercontent.com/theislab/ehrapy/feat/stratified-table-one/docs/_static/docstring_previews/stratified_table_one.png)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `abd072c5a049`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.