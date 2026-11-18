# Issue

**Title:** Flipping bug 🐞

## Description

In the current version of emperor, if you flip the orientation of one of the axis, you may end up in a situation where the range data lies outside of the current axes. To remediate this, the `dimensionRanges` properties are updated to reflect the new range that the data spans. Additionally, we need to keep track of when an axis is reoriented, so we know when change the ranges back in a situation when we are swapping out a _flipped_ dimension.

I've also improved the test cases to reproduce the problem.

---

This one took longer than I was hoping. 😫

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `504d99300f69`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.