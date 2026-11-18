# Issue

**Title:** Fix setup.py from merge

## Description

This PR fixes the setup.py installation from a recent merge.

`python3 setup.py sdist bdist_wheel` shows what files get bundled up into the package.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb03218ee5cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.