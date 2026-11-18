# Issue

**Title:** Switch external resources workflow to mamba

## Description

The conda environment for the external resources no longer builds in GitHub Actions.  See a [recent build failure](https://github.com/greenelab/covid19-review/runs/6734550792?check_suite_focus=true).

I'm following https://github.com/conda-incubator/setup-miniconda#example-6-mamba to try to use mamba instead.

We may have to merge, test, and repeat until this works.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0bb83a5d2a9c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.