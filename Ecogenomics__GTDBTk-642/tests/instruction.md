# Issue

**Title:** fix: update masked sequence conversion

## Description

Fix for #641 
Change masked_seq conversion from .tostring() to .tobytes() for compatibility with numpy=2.3.0

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `86786a0e2ff0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.