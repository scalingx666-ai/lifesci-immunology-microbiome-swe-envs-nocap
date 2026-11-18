# Issue

**Title:** Run PCA and FAMD on longitudinal data by unfolding timepoints

## Description

`ep.pp.pca` and `ep.tl.famd` now run on 3D `.X` by unfolding every variable and timepoint into a feature (unfolded/multiway PCA), storing the embedding in `obsm` and loadings of shape `(n_vars, n_t, n_comps)` in `varm`. Together with `ep.pp.neighbors` defaulting to `X_pca` for longitudinal `.X`, pca, neighbors, umap and leiden work on longitudinal data without summarizing it first.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fec8b8cd439f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.