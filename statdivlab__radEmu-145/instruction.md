# Issue

**Title:** add `na.rm` behavior to pseudohuber median and make small fix to micro wald procedure

## Description

add `na.rm` parameter to `pseudohuber_median` and `dpseudohuber_median_dx` that acts like `na.rm` in `mean` - as mentioned in issue #137

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca85f3e2a2d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.