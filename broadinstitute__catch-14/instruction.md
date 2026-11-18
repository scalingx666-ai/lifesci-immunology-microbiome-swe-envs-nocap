# Issue

**Title:** Expose option to specify a custom hybridization model

## Description

Previously, a user could define a function in CATCH that implements a custom model to determine whether a probe hybridizes to a region of target sequence (e.g., to incorporate a calculation of free energy). The user would then need to set the `cover_range_fn` parameter where necessary (e.g., in the `set_cover_filter` module) to use this custom function.

This pull request makes it easier to use a custom function that determines hybridization. It exposes this ability by adding the `--custom-hybridization-fn` argument to the main `design.py` executable. (Likewise, it adds an argument for a more tolerant function to use with blacklisting genomes and differential identification.) The argument provides a path to a Python function, and CATCH dynamically loads this and uses it whenever it calculates hybridization between a probe and target sequence.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe63b86bc413`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.