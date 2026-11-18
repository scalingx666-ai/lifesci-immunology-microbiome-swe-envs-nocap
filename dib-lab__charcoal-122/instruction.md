# Issue

**Title:** try evaluating GTDB contamination

## Description

Taking a stab at #121!! This uses `search --containment` instead of `gather`, and removes identical matches, before doing its thang.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `189f33ccf030`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.