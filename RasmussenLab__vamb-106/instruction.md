# Issue

**Title:** aae implementation with interface equal than vamb

## Description

This version of aae contains all models (encoder, decoder, discriminator_l, discriminator_y) defined as functions of the same class.
However the optimization process slightly differs with the one from the original aae.py, which was used to create all the figures from the manuscript.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c0935213183`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.