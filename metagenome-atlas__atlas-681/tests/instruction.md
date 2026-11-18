# Issue

**Title:** Convert mem_mb value from gb to mb for select rules

## Description

A few rules had been using the mem value directly from the config.yaml to set the mem_mb resource without converting from gb to mb (by multiplying by 1000)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1314e3139575`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.