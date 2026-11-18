# Issue

**Title:** Disable multiple arguments and clarify how to ask for help

## Description

This small PR does two things:
- Clarify how to seek for support in the readme and in the contributing section of the documentation. This follows the issue #20 
-  Disable the possibility to give multiple time the same argument in CLI resulting in overwriting their value. Now, arguments have to be given only once otherwise a clear error is thrown. This follows a problem faced in issue

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe755d1e20f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.