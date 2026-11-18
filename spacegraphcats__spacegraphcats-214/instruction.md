# Issue

**Title:** [WIP] start making spacegraphcats usable from a pip install

## Description

This PR refactors things to make spacegraphcats pip-installable and more usable by others. This is mostly munging about with entry points, setup.py, etc. etc.

It also enables some nice examples, which I've broken out into two repos: 

* a basic example: https://github.com/spacegraphcats/spacegraphcats-dory-example
* a more complete/thorough example + Snakemake: https://github.com/spacegraphcats/spacegraphcats-twofoo-example

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `03ccd0aea2be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.