# Issue

**Title:** Bugfix: Convert paths to str before passing to pycoverm

## Description

Commit 3a2c3e2 made more extensive use of types, including the proper Path types for paths passed to pycoverm.
Unfortunately, pycoverm expects strings, so this made Vamb crash.

This was not caught in tests which suggests we need to add integration tests to the suite, probably by reviving the "result tests".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `910f64c9fc29`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.