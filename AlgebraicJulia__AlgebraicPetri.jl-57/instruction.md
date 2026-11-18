# Issue

**Title:** 0.7.0 release

## Description

This PR provides a minor bug-fix in the BilayerNetwork conversion function, and increases the AlgebraicPetri version for the 0.7.0 release, which includes the addition of the following features:

- Added Requires.jl to reduce unnecessary dependencies
- Added Docstrings to core functionality
- Added BilayerNetwork tooling and conversion to and from Petri nets
- Added interop tooling with Catalyst.jl

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `537728460cfe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.