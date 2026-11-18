# Issue

**Title:** Add macOS 26 support

## Description

Add macOS 26 package mappings and share ParaView package selection. Repair known macOS ROOT library paths and accept the C++23 ROOT package while keeping BioDynaMo at C++17. Add macOS 26 to both CI matrices.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62cd675a8f7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.