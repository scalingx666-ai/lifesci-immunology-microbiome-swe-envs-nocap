# Issue

**Title:** Use a dask-native PCA solver for dask arrays by default

## Description

`ep.pp.pca` now defaults to scanpy's `covariance_eigh` solver for dask arrays instead of dask-ml's PCA, which ehrapy does not install. This fixes the CPU tests on main, which fail since #1158 on the 3D dask PCA test.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01394957c6dc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.