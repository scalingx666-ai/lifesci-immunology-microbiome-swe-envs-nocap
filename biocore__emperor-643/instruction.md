# Issue

**Title:** ENH: Warn users when hiding samples from a plot

## Description

This patch adds a message (in the sample counter) stating that hiding
samples in an ordination can be misleading.

 

Example animated gif:

![emperor](https://user-images.githubusercontent.com/375307/36567151-79a64712-17da-11e8-8bcf-935a6b61e339.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45b1437c9e5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.