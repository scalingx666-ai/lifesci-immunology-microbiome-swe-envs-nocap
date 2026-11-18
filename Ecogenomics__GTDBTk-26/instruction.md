# Issue

**Title:** Bug in the parser of fastANI

## Description

posssibly a version change in fastANI leads to a parsing error, changing the split(" ") to split() fixed it

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1dca9540818f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.