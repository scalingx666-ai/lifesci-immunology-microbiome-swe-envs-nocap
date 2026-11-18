# Issue

**Title:** ENH: Link emperor double-click event and add timer cancelation

## Description

This adds the ability to double-click on a color category in Emperor and highlighting the tips in the tree represented by that group. This also adds a timer cancellation to prevent problems with sample selections as reported in #197.

![double-click](https://user-images.githubusercontent.com/375307/92145140-a4125e80-edcc-11ea-8f90-65db9e7536ec.gif)


The documentation on the callback is fairly lax but should be improved once the explanation in #319 is merged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d19f0dfd244`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.