# Issue

**Title:** Update CI workflows

## Description

Some workflows used old action versions, and the conda recipe check was silently broken: it installed Binette with Python 3.8, although Binette needs 3.12 or later, and it ran on the retired `macos-13` runner. The lint workflow also didn't check the tests.

### Changes
- Lint and format: ruff now checks `binette` and `tests`. The ruff version is pinned to 0.13.3, the same as in `.pre-commit-config.yaml`.
- All workflows use the same, current action versions: `checkout@v7`, `setup-python@v7`, `setup-miniconda@v4` and `upload-artifact@v7`.
- Conda recipe check: now uses Python 3.12 and `macos-latest`, only the `conda-forge` and `bioconda` channels, and `conda install` instead of mamba.
- Main CI: removes the `defaults` channel and a commented-out micromamba block.
- Release: the publish step is renamed from "TestPyPI" to "PyPI", which is where it actually publishes.
- Main CI runs on `ubuntu-24.04` instead of `ubuntu-latest`. Ubuntu 26.04 (now `ubuntu-latest`) can't load the tensorflow build that CheckM2 requires (conda-forge/tensorflow-feedstock#455).

### Notes
- Python 3.13 is not added to the test matrix. CheckM2 1.1 requires tensorflow `<2.20`, which has no Python 3.13 build on conda-forge.

This has been implemented with the help of Claude Code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10226fc534a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.