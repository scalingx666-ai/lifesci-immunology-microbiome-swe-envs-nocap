# Issue

**Title:** fix(memorymapped): allow fd 0 on linux

## Description

When stdin is closed, `open()` might return fd 0 on linux. This PR allows fd 0 as a valid file descriptor.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18d8ddc2f468`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.