# Issue

**Title:** add conda environment.yml

## Description

cartopy isn't reliably pip-installable without some manual pre-install steps, and the docs recommend using conda. This gets the repo working on Binder.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2b5e04e8bb6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.