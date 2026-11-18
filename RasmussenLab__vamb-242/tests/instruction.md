# Issue

**Title:** Print help if only typing `vamb bin`

## Description

Previously, `vamb bin` would cause an internal parser error. Now, instead, do the same as `vamb bin -h`, i.e. print the help, and exit with error code 1.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a8a66df7831`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.