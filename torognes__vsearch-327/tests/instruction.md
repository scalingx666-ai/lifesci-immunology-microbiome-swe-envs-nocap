# Issue

**Title:** Updating CFLAGS

## Description

Updates CFLAGS for autotools to correctly enable CPU features.

On Mac OS 10.14, GCC shipped with Xcode fails to enable SSSE3 with default configuration. Issue is solved with the addition of `-march=native` flag.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `526d2d510392`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.