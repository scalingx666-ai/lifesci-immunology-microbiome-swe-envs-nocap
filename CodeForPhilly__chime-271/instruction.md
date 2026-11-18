# Issue

**Title:** Fix inputs

## Description

All the inputs are broken.

Original code assumed that the result of the st.xyz_input call was a widget. It is actually the widget's updated value from the user, so the user's updated values were being lost.

  (while adding even better bugs)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `224120f4a0a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.