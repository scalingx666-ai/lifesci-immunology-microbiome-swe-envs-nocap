# Issue

**Title:** Optimized SAM parser

## Description

This simple tweak reduced runtime from 6.86 s ± 25.2 ms to 4.93 s ± 4.12 ms on a real SAM file.

It can be further optimized using function reference reassignment so that it won't check header (@) every time.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f86ca188c090`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.