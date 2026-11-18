# Issue

**Title:** Update Singularity to install CMake 3.19.3 for compatibility

## Description

This pull request pins CMake to version 3.19.3 on Singularity file to avoid issues with newer versions (CMake 4.x).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18d74339fc70`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.