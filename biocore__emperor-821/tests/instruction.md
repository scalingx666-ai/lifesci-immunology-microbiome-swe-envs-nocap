# Issue

**Title:** Update Python unit tests for new version of Pandas and fix CI workflow

## Description

These changes should allow the GitHub "Emperor CI" workflow to succeed again. They remove Python 3.7 (now EOL) from the test matrix, apply a workaround to get PhantomJS to work on the newest `ubuntu-latest` runner, and update the Python unit tests to work with new versions of Pandas. They also fix the `notebook` dependency to `<7`, since Jupyter 7 uses an incompatible extension system based on Jupyter Lab's.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fbaa4a96c591`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.