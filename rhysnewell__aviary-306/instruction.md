# Issue

**Title:** Add checkm2 feature with activation environment configuration

## Description

After the updating of all packages, numpy within requirements.txt increased to 2.4.1. When running the mock sample test say that i was running into the error "A module that was compiled using NumPy 1.x cannot be run in NumPy 2.4.1 as it may crash." Within checkm2. Tried to pin version <2.0 within checkm2 dependencies, however NumPy leakage was causing 2.4.1 still to be present after stating <2.0. Changed activation to PYTHONNOUSERSITE=1 to stop the env from overriding. Afterwards package ran normally.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5255310c69e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.