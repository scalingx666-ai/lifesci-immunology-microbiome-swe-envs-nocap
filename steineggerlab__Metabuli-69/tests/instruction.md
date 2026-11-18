# Issue

**Title:** Fix bugs

## Description

Fixed bugs
1. During `build` workflow, --buffer-size > INT_MAX caused a problem. It is fixed now
2. Reads shorter than a k-mer sometimes caused a memory issue. Fixed now

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84e4e13b1ab9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.