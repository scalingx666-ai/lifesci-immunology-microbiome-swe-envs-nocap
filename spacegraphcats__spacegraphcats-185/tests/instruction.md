# Issue

**Title:** [MRG] Trim low abundance

## Description

`bcalm_to_gxt.py` now removes pendant vertices with abundance 1 by default; this behavior can be revoked with the `-P` flag.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f35fc1c26581`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.