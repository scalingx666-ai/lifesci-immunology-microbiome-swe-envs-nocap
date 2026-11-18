# Issue

**Title:** Fix normalization of the diffusion gradient

## Description

Even if gradient.IsZero() is false, gradient.Norm() can evaluate to 0.
e.g. if gradient is: {0, 0, 1.4013e-45}

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5531d9ffa5b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.