# Issue

**Title:** Remove the single-cell leftovers feature_symbols, use_raw and unused settings

## Description

The `ep.pl` and `ep.get` functions no longer take `feature_symbols` or `use_raw`, and `ep.settings` keeps only `verbosity` and `n_jobs`, the two fields ehrapy actually reads. Plots now always read `.X` or `layer` instead of silently switching to `.raw` when it is set.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6ef31a3ea49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.