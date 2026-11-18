# Issue

**Title:** Stick to bbmap version 37.17

## Description

Bbduk2.sh seems to be removed in the latest version, so with this fix it is still present.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66c87daffbb2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.