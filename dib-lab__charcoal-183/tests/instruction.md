# Issue

**Title:** [MRG] update snakemake and other dependencies

## Description

Updates python to >= 3.7, pins snakemake to 6.4.1, and click to <8. Also adds `mamba` to the default install. Reconciles setup.py and environment.yml.

Addresses problems discovered in  among other things.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `94f69c85c647`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.