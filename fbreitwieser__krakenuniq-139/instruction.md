# Issue

**Title:** Fix: Add "file" to Dockerfile

## Description

KrakenUniq script `read_merger.pl` does not work as intended if `file` is not present in the execution environment, which leads to empty report files because input data could not be processed and KrakenUniq does not exit when this happens which unfortunately masks this error.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d71fd574ea9c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.