# Issue

**Title:** remove the `call.` argument to `message`

## Description

in `control.net` `message` is called with a `call.` argument. As it is not a named argument to `message`, the value is concatenated to the message string.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b9b19ae03afa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.