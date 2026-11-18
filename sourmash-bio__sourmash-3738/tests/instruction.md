# Issue

**Title:** CI: update to cibuildwheel 3.1.1

## Description

- Base image for manylinux wheels changed, now it is based on AlmaLinux 8 (for `2_28`).
- Update configs to install and use libclang as AL8 expects.
- Pyodide still not working, but update CI definition to use `if: false` and avoid commenting out code

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e471bf5eedd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.