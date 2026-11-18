# Issue

**Title:** Add longitudinal quality control to qc_metrics and qc_lab_measurements

## Description

For 3D data, ep.pp.qc_metrics now adds how often and how regularly every variable and observation is measured, in the times of tem[time_key], and ep.pp.qc_lab_measurements flags implausible jumps between consecutive values as {var}_jump in obs, beyond a given max_change per time or else beyond the range of normal changes estimated with method. 2D outputs are unchanged and both stay lazy for dask with a single compute.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56eb3f9e832a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.