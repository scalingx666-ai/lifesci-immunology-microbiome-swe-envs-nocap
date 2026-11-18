# Issue

**Title:** Allow setting random seed from command line

## Description

We currently default to seed 0, but some uses may want to use random seeds. Note that Vamb behaviour is not guaranteed to be preserved even with the same seed, because a) PyTorch is nondeterministic at this point, and b) We do not care to fix the versions of NumPy to prevent updates to the underlying RNG.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `89881a77c4d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.