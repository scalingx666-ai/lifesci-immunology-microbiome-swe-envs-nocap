# Issue

**Title:** Upgrade gtest

## Description

Upgrade gtest from 1.11.0 to 1.17.0. The older version used an cmake version which is not compatible with newly released cmake 4.x. This broke the CI about a month ago. This PR should fix the CI and ensure that BioDynaMo builds with cmake 4.x.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6bd25823775`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.