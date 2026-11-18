# Issue

**Title:** Fix warning in multi-simulation mode

## Description

The check of whether real data was present in our Database class
was always evaluating to true, because it was an object on the
stack. Changed that into a pointer, so that can be evaluated for
nullptr when no Database object is created

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c884685c28b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.