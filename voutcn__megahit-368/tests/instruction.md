# Issue

**Title:** Add support for non-x86_64 architectures (e.g. Linux ARM64)

## Description

Fixes  
Based on: 

Preserves the x86_64 specifics when building on x86_64 machine

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f329c6d24a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.