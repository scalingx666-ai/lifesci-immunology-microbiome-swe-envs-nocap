# Issue

**Title:** Store the time series metric of neighbors by name

## Description

`ep.pp.neighbors` with `metric="dtw"`, `"soft_dtw"` or `"gak"` now stores the metric name in `uns["neighbors"]["params"]` instead of the internal distance function with the whole time series array, so that `ed.io.write_h5ed` can write the result.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d6b648c6eea6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.