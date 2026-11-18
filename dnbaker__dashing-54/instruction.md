# Issue

**Title:** Dependency

## Description

1. Includes components with external submodules directly for faster installation. (Response to .)
2. Provides error messages for sketch finalization, including an update to the sketch library for saner defaults when Shrivastava-style densification of empty sketches. (Addresses .)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc5877255e3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.