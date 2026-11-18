# Issue

**Title:** BUG: Fix styling problem in the Jupyter 📓

## Description

Turns out Jupyter sets some styling on the cells of the HTML tables,
with these few changes those settings are removed.

Additionally, the colorpicker for the background was being set as white
by default, this should also fix that problem.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `82bade09f0fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.