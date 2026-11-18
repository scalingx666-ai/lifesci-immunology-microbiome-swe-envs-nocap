# Issue

**Title:** Switch-to-self-hosted-runners

## Description

This pipeline has quite a few tests consuming about half our runners per PR. This should lighten the load and overall speed up CI tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f7c97e3c6ee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.