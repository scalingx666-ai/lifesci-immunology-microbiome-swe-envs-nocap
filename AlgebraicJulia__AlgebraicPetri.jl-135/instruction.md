# Issue

**Title:** perf: use native package extensions in julia 1.9+

## Description

This adds support for using native package extensions that are now in Julia v1.9+ with AlgebraicPetri for the modeling framework interoperability while maintaining backwards compatibility with older versions of Julia using Requires.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9015dae8bae8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.