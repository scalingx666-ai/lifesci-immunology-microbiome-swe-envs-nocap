# Issue

**Title:** Switch to ordered map for reproducible outputs

## Description

Hi,

as mentioned in  - switching
to an ordered map here makes sure the `_classification.tsv` output file is identical between runs (with same 
parameters).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0c807ec175b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.