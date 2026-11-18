# Issue

**Title:** [MRG] Update dib-lab software dependencies; fix warnings

## Description

* update sourmash to 4.0.0rc1
* update snakemake to latest release
* reconcile setup.py with environment.yml
* add -Werror to find deprecations

TODO:
- [x] fix import order error
- [x] fix pytest mark errors?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e07f5729ca43`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.