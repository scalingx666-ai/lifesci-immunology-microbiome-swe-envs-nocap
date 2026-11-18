# Issue

**Title:** Add timing to verbose

## Description

updating emuFit() when verbose = TRUE to not only report which test is running, but also report when it completes and how much time it took (either rounded to either seconds, minutes, or hours depending on how long it has been)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a93d1128613`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.