# Issue

**Title:** [MRG] close databases and files appropriately

## Description

Over in  some tests were failing because of my bad coding practices - specifically, my failure to properly close sqlite databases and output files. I fixed the problem there, but since that might not get merged soon, I decided to put these fixes up as a separate PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aabd67104f50`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.