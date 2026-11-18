# Issue

**Title:** Windows

## Description

Optimizing for Windows OS support.

Changes are mainly
- not using std::map & std::unordered_map
- not using std::vector or reuse it

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed609df8d5f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.