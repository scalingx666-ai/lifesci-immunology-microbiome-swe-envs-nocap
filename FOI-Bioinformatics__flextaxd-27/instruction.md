# Issue

**Title:** Bug fixes 20201029

## Description

Update on Kraken2 issue, the format is only usable by bracken, kraken2 still requires 1-2 extra empty columns at the end to not trim off node names. Reverted and bracken output option added

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c2de7858c77`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.