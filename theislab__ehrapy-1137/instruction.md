# Issue

**Title:** Sum sparse observation totals with fast_array_utils

## Description

`qc_metrics(qc_vars=...)` now computes per-observation totals of scipy sparse arrays and dask arrays with sparse chunks with `fast_array_utils.stats.sum`.
Dask arrays with sparse chunks are reduced blockwise instead of being rechunked to hold all variables per block.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb4015055d93`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.