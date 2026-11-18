# Issue

**Title:** Disable D-adaptation for AVAMB

## Description

Since around the D-adaptation commit, the avamb tests have begun failing.
It looks like the AAE doesn't really work with D-adaptation.
Instead of digging into this, I've decided to just revert the D-adaptation
for the AAE in particular.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `40b19af03ceb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.