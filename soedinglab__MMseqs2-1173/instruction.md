# Issue

**Title:** Update CI for zlib download url

## Description

## Summary

- CI failed from `wget` 404 failure. Looks like URL changed by provider.
- Apply working URL of `zlib` for same version.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d0185a2d3478`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.