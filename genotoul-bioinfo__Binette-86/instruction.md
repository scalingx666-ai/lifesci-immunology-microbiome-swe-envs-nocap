# Issue

**Title:** Remove checkm2 github link from pyproject.toml

## Description

Pypi deployement fails because of the github link in the dependencies in the pyproject.toml.

This PR simply remove the link of checkm2.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c600128472f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.