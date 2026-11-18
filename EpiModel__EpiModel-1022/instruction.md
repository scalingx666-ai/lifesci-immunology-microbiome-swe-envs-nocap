# Issue

**Title:** fix random params get

## Description

## Summary

Fixes preservation of per-simulation `random.params` draw metadata after subsetting or merging `netsim` objects.

Previously, `get_sims()` updated `control$nsims` and sliced simulation outputs but left `param$random.params.values` unchanged, causing `get_param_set()` to error or report stale draws. `merge.netsim()` also compared realized random draws when checking parameter compatibility and retained only the first object's draw history. This PR subsets/appends those draw histories correctly and handles one-simulation outputs with vector-valued random parameters.

## Testing

- Targeted `test-get.R`
- Targeted `test-merge.R`
- `R CMD build .`
- `_R_CHECK_FORCE_SUGGESTS_=false R CMD check --as-cran --no-manual EpiModel_2.6.1.tar.gz`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f05c677f6d07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.