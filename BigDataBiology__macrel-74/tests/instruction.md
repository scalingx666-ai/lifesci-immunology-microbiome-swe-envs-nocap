# Issue

**Title:** FIX float counts in Paladin mapping

## Description

Paladin mapping does some frame-shitfs and probabilistic alignment, which leads to fractional weights propagating into SAM/BAM files. To fix that:

- sam filtering to avoid this problem keeping only uniquely mapped matchers

- count should consider only uniquely mapped matchers.

- dowgraded version and IR version of onnx models to wider compatibility

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c59432be7644`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.