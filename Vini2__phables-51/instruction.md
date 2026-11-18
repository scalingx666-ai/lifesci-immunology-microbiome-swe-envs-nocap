# Issue

**Title:** Adding dockerfile

## Description

This PR adds a dockerfile which allows you to run `phables` either from docker (but you need root) or singularity. There are a couple of tricks mostly associated with ensuring you correctly mount remote directories in the right places, but the README clarifies those steps.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f03084178123`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.