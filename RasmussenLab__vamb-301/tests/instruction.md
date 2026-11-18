# Issue

**Title:** Mask out low bits of input float arrays

## Description

Float32 has 23 bits of precision, which is more than necessary for Vamb. We can mask out the lower bits, probably with no loss of performance. This helps reducing the disk space usage of Vamb's output.

It almost certainly won't cause a regression, but let's test it nonetheless.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a9d06162be7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.