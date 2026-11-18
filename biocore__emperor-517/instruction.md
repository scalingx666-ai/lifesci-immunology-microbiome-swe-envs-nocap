# Issue

**Title:** ENH: Add support to plot 🐼s DataFrame objects

## Description

This PR adds a helper function, `scatterplot`, that can take as only argument a
Pandas DataFrame and returns an Emperor object. The function itself
extracts the numerical data from the DataFrame and creates a dummy
OrdinationResults object.

Note that this is a rather experimental feature, so testing/suggestions are
very welcome.

This PR depends on #516 so merge that PR first.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97211e458c24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.