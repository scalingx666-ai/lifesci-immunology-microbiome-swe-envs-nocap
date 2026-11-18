# Issue

**Title:** Handle obs name clashes and missing values in detect_bias

## Description

ep.pp.detect_bias and ep.tl.rank_features_supervised no longer fail when a variable shares its name with an obs column or has missing values, because they read variables from X directly and leave out observations without a value of the predicted variable or sensitive feature. This makes bias detection work on PhysioNet 2012, whose Age and Gender are both obs columns and variables.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `54e337a1c70b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.