# Issue

**Title:** Fix scheduled GHA

## Description

The scheduled GHA are configured with `-Dtest=off`. One of the shell scripts tried to execute `./build/test-sim-test` which is not built when `-Dtest=off`. This PR adds an `if` statement to check if `build/test-sim-test` exists and only if that's the case, we execute the "problematic" command.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6eec8a65ed27`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.