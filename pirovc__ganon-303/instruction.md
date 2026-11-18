# Issue

**Title:** Feature/modernize infra

## Description

- Use [pyproject.toml](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/#) in replacement of `setup.py` with automatic versioning [setuptools-scm](https://setuptools-scm.readthedocs.io/en/latest/)
- Fix and improve travis

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `524537d31a49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.