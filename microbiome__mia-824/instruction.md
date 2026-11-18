# Issue

**Title:** Generalise agglomerateByModule to non-binary numerical modules

## Description

Hi!

Recently ariadne started supporting numeric matrices describing how much each feature coverage each module (module coverage). So I updated `agglomerateByModule` to also accept this kind of numeric non-binary matrices.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fafaeb560e7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.