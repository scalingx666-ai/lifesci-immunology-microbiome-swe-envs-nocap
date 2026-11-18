# Issue

**Title:** ENH: Add support for custom axes

## Description

This addition resuscitates the old implementation from
make_3d_plots.py/make_emperor.py to deal with 'custom axes', however moving
forward we hope that this feature will be available from the user interface.

cc @gregcaporaso

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3447ca06bc99`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.