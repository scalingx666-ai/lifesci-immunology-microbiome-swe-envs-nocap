# Issue

**Title:** Zero hit BAM profiling fixy

## Description

TIL that the commit 943655508 broke profiling of BAM files with 0 hits. which is quite a common need in large surveys. changes here fixes the issue while maintaining the pre-filter functionality as @FlorianTrigodet intended originally.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eedc29b9d482`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.