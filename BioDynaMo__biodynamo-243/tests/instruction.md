# Issue

**Title:** Add SWC export for neurons

## Description

SWC is a file format that is typically used to store neuron morphologies. While we already have ParaView at hand, the SWC file format establishes the interface to other third-party libraries (e.g. NeuroM of the EPFL) commonly used in that field.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8439cf3d8351`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.