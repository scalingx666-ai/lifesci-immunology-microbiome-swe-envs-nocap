# Issue

**Title:** move all checks that were at the beginning of `emuFit()` function to a separate function, `emuFit_check()`

## Description

I made this update in order to have a clear place for all checks on the arguments to `emuFit()` (so that the `emuFit()` function doesn't get longer and longer as arguments are added and need to be checked), and so that I can call this function from the `fastEmu` package instead of separately implementing the same checks in that package

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2817ba4a971`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.