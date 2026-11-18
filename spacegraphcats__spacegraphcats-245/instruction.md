# Issue

**Title:** [MRG] add unlock to command line

## Description

Adds `--unlock` parameter to the command line to allow [unlock of snakemake processes](https://snakemake.readthedocs.io/en/stable/project_info/faq.html#how-does-snakemake-lock-the-working-directory). Addresses #221. 

Note this still needs to be tested before merge, as spacegraphcats installations were failing from master when I added this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a74505428d3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.