# Issue

**Title:** Raise KeyError for unknown variable names in imputers and normalizers

## Description

The imputers and normalization functions now raise a `KeyError` naming variables that are not in `edata.var_names`, via a shared `_var_indices` helper. Previously `get_indexer` returned -1 for unknown names, so `ep.pp.simple_impute(edata, var_names=["nope"])` silently imputed the last variable and `ep.pp.explicit_impute` ignored unknown `replacement` keys.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c83f489dca9c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.