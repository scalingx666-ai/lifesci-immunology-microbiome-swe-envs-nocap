# Issue

**Title:** Add type-hints to interventions.py

## Description

Makes it a bit easier for your editor to perform autocompletion and goto-definition.

Before this change, it didn't work for me in VS Code (with venv) when trying to look up `sim.t`, but now it does :tada:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cfc73005f97a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.