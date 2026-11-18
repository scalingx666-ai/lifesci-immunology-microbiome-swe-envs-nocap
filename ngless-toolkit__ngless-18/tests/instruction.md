# Issue

**Title:** Fix samtools tests and add ability to test command line arguments

## Description

Fixes running samtools tests on a system without 'samtools' in $PATH.

It also expands the parallel test to cover the use-case described in #17

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d22a79eaf8ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.