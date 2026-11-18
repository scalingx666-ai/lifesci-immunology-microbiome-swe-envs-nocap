# Issue

**Title:** Fix bug with running standalone version; account for NumPy dependency in standalone install instructions; a few small changes w/r/t node circle options

## Description

There's a line in `_plot_utils.py` that imports `q2templates`, a package which is (usually) only available in QIIME 2 conda environments. This was breaking the standalone script when ran outside of a QIIME 2 environment.

To fix this, we can just move the import down so that it's only done if EMPress is being run through QIIME 2. This fixes the problem.

A very warm thank you to @ammaraziz for pointing this out!

Edit - I also made a few changes in this PR's later commits that make the UI for changing the node circle behavior a bit nicer. Should be limited to just cosmetic changes to the HTML.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c0b857ce894`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.