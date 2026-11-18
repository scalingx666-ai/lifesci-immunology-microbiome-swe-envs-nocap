# Issue

**Title:** Add a Binder badge

## Description

Hi!

I added a badge for running Binder for the paper notebooks, and also an `environment.yml` file with the dependencies. I kept scikit-learn in version 0.19.2 because the random forest classification example breaks on 0.20 (because cross_val_score was [moved to another module](https://scikit-learn.org/0.19/modules/generated/sklearn.cross_validation.cross_val_score.html))

Here is a temporary link pointing to my branch while it is not merged: [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/luizirber/hulk/binder?filepath=paper%2Fanalysis-notebooks)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `773cab741afa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.