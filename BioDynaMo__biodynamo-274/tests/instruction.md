# Issue

**Title:** Update GHA for macOS and fix notebooks on Ubuntu

## Description

- Remove deprecated macOS 10.15 from GHA
- Add runner for macOS 12
- Change in build system to support `11.7` 
- Fixed version of python packages to fix notebooks on Ubuntu
- Removed notebook test from `CentOS7` because no one uses notebooks on CentOS7

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe34ced0f537`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.