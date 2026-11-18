# Issue

**Title:** Do not error with too small batch size

## Description

In recent versions of PyTorch (perhaps all versions), having a batch size larger than dataset size is not a problem. So, the error that Vamb threw had no purpose, and just caused problems for our users.
Instead, display a warning if Vamb is trained on too few sequences.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33fbca1ba944`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.