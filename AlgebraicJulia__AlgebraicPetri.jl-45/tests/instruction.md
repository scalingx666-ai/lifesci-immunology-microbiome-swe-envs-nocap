# Issue

**Title:** Conversion Tooling to Catalyst

## Description

This PR provides tooling for converting from PetriNets to the Catalyst ReactionSystem object.

This allows us to take advantage of the Catalyst parameter estimation tooling once the petrinet is constructed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2d1942045b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.