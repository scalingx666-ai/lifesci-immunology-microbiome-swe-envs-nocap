# Issue

**Title:** feat(ci): add whitespace stripping to style workflow

## Description

If it was supported by RStudio, which is used by the majority of users, I think it's a good idea to include .editorconfig (https://editorconfig.org/).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be708a734fe6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.