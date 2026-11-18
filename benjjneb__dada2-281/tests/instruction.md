# Issue

**Title:** Handle mclapply under Windows

## Description

Simple fallback with `mc.cores=1` for Windows OS.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0528966bbc41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.