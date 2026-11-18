# Issue

**Title:** Pin scikit-learn version to 0.19.2 in setup.py

## Description

This , in which mismatched versions of scikit-learn could cause errors/warnings when loading models using pickle.

It looks like [the bioconda recipe](https://github.com/bioconda/bioconda-recipes/blob/master/recipes/eukrep/meta.yaml) for EukRep already pins the scikit-learn version to 0.19.2, which addresses this problem for conda EukRep users. This PR pins the version in the setup.py file as well, which should address this problem for pip EukRep users.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c86d1e9079b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.