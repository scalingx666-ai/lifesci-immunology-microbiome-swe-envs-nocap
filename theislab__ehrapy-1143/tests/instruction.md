# Issue

**Title:** Accept obs-only calls and time series neighbors on 3D .X

## Description

Plots, causal tools and `ep.pl.dendrogram` no longer reject 3D data when they only use `obs` columns or a precomputed dendrogram, and `ep.pp.neighbors` uses the 3D `.X` by default with the time series metrics. Euclidean neighbors and `ep.tl.rank_features_groups` on 3D data now raise the shared 2D-only error that points to `ep.pp.summarize_measurements` instead of a scikit-learn error or a custom message.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b776350f2a87`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.