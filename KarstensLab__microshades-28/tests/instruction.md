# Issue

**Title:** Resolve legend / plot warnings

## Description

Hello,

This pull request proposes changes to resolve the following:

- [x] Warning when creating a custom legend. `Warning: Multiple components found; returning the first one.`.
- [x] Warnings when generating barplots with `plot_contributions`: `Adding missing grouping variables: 'Sample'`;`summarise() has grouped output by 'Sample’.`.
- [x] Issue with `plot_contributions` that displayed the median barplot incorrectly.

These changes were tested with the microshades GP vignette.

Thanks!
-Anagha

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c31eac7b21fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.