# Issue

**Title:** Fix list_special_params

## Description

`list_special_params` is an internal function of EpiModel (never exported). It is called only in 2 places. The cleanest fix was to change it's input to be parameter names instead of th parameter list.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6c32ed2a51f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.