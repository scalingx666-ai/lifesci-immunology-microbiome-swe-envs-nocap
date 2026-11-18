# Issue

**Title:** [Fix] Get correct number of header entries for subject sequences

## Description

For translated databases, the number of original sequence lengths was used to determine the header entries. The last entry of the original sequence lengths is however the sum, so one empty header line was accidentally created in this case.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f36e9396924`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.