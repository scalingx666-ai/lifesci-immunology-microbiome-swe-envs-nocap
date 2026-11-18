# Issue

**Title:** [MRG] clean up some unused code in index_cdbg_by_multifasta.py

## Description

Fixes 

This PR removes some unused/confusing code for specifying ksize and scaled in `index_cdbg_by_multifasta.py`.
* `ksize` can be inferred from the k-mer index, which it needs to match anyway
* `scaled` isn't used at all, and is a remnant from whence this script came

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f23e9abc4b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.