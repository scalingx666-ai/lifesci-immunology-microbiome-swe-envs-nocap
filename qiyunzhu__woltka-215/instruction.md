# Issue

**Title:** Upgrading Python packaging mechanism

## Description

The followin changes were made:

1. Let Click CLI import workflows in a lazy manner, which significantly accelerated loading.
1. Used `pyproject.toml` instead of `setup.py` for build configuration.
2. Used hatch instead of setuptools as the build backend.
3. Used `environment.yml` instead of `conda_requirements.txt` for conda configuration.
4. Added MacOS and Windows to the CI OS matrix.
5. Added 3.10 to the CI Python version matrix.
6. Removed the "tools" submenu.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `959f2f999375`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.