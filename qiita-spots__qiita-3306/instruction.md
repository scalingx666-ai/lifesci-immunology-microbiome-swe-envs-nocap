# Issue

**Title:** resource allocation

## Description

These are the code base changes to support the new resource allocations; something that I wasn't aware was that we didn't support walltime formulas, only memory - now we do.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `027613fef9d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.