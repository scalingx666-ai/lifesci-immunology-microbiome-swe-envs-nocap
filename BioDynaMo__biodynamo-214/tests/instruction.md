# Issue

**Title:** Resize locks vector in diffusion grid if the size changes

## Description

Resizing happened only in the `Initialize` method.
Therefore, out-of-bounds accesses happened if the grid grew 
during the simulation.
If the out-of-bounds value was not zero, the lock appeared
to be hold by a thread which caused deadlocks.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7c8faa5d4a82`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.