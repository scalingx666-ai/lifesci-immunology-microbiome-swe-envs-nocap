# Issue

**Title:** changed conda channels

## Description

Changed
- channels from `anaconda` to `conda-forge` 
- changed `biopython` channel to `conda-forge` 
- use conda by default 
- missing `biopython` requirement in `simulate_reads_wgsim` process

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a6e7ccaa022`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.