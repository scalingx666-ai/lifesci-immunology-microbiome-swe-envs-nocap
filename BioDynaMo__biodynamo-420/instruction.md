# Issue

**Title:** Update Style Guide Checks to Run on Ubuntu 22.04 Instead of 20.04

## Description

This pull request updates the workflow condition in .github/workflows/ubuntu-ci.yml so that the style guide checks are executed when matrix.os is ubuntu-22.04, instead of ubuntu-20.04.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `569b4b79a50b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.