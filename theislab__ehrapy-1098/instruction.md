# Issue

**Title:** Docstring examples: use 3D .X instead of .layers["tem_data"]

## Description

Addresses the docstrings checkbox of #1093.
Docstring examples keep time series in the 3D `.X` instead of `.layers["tem_data"]` wherever the function reads `.X`, and every touched example matches the current API and shows the output it actually produces.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0058c08bf2cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.