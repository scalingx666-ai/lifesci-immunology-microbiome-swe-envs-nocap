# Issue

**Title:** BUG: Fix problem with axes labels

## Description

Label names are now fixed to account for scikit-bio's OrdinationResults IO
module. The UI for the axes names has now changed to allow users to click on
menus and checkboxes (like in the previous version of emperor) instead of
clicking on the scree plot.

The variation explained by each axis is now shown **only** for non-custom axes.

While the scree plot interaction was *fun*, I think it was a bit confusing, so
I think this is better.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31ba9597a83b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.