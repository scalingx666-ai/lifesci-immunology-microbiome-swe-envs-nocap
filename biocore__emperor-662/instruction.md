# Issue

**Title:** BUG: Hide edges when hiding visible samples

## Description

For procrustes plots edges were not being hidden when samples in it were. Demo:

![procrustes-bug](https://user-images.githubusercontent.com/375307/38704852-a4804264-3e75-11e8-8001-7e1cab8a8740.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `104d3551defd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.