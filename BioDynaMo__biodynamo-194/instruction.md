# Issue

**Title:** Fix Norm and Normalize for zero vector

## Description

The `MathArray.Norm()` method returned 1.0 for the zero vector which may not be what users expect. Now it returns 0. As a consequence, `MathArray.Normalize()` will not work for zero vectors any longer which is why we now throw a **_Fatal_** if someone tries to normalize the zero vector. See discussion on slack.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c117fc04458f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.