# Issue

**Title:** BUG: Disable arrow keys from the OrbitControl object

## Description

When editing text in the notebook and using the arrows to navigate, the
OrbitControl object would listen to those events and pan the plot around.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `957f2e389662`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.