# Issue

**Title:** Limit medoid cache size to 64

## Description

The medoid cache stores at least 4 * n_contigs bytes per entry, and often much more. Without a limit, it may quickly consume multiple gigabytes of memory. Here, restrict the size to 64, which is approximately 3 times the size of the latent space.
That might be too generous a size, but it should solve the problem experienced by our users at the moment.

May possibly solve #401

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f028bdd6119c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.