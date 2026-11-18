# Issue

**Title:** Remove scanpy mentions from the docs

## Description

Removes the remaining references to scanpy from the API docs and docstrings, so users are pointed to ehrapy functions instead of scanpy settings, classes and documentation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e270043df90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.