# Issue

**Title:** [MRG] add `mamba` as a conda dependency, b/c snakemake wants it.

## Description

Fixes  by adding `mamba` to environment.yml.

Also updates python deps - snakemake to `=7.3.8`, and click to `>=8.1.2,<9`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3af471e518ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.