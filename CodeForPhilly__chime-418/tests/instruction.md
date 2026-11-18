# Issue

**Title:** Allow the user to prescribe mitigation date

## Description

This is on top of various cleanup and refactoring in #415, so probably review that first.

There's a potential edge case if distancing is strong enough to cause a dip in the census curve, that prescribed-doubling fitting of first-hospitalization might align to a point on either side of the dip.

I've tested this manually and it seems to behave as expected, but I don't have a great handle on how to really validate it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6ff8aaa0be2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.