# Issue

**Title:** Fixes v. 0.0.10 bugs

## Description

This PR fixes the following issues:
- #90 

The filtering is ignored if the transformation/filtering is done before running tempted.

- #83 & #87 

The HTML files are not packaged with the release in the setup.py.

- #82

If no-centering is done then the original table list is used.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `190f89ee48fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.