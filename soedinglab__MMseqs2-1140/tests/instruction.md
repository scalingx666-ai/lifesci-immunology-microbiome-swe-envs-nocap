# Issue

**Title:** Fix E-value truncation in iterative profile search

## Description

## What was happened

Iterative searches of sequence queries against profile targets stored the original E-value threshold as an integer.
Values such as 0.001 became 0, causing the final iteration to reject new hits with positive E-values.

## Fix
Use double to preserve the requested threshold. (`par.evalThr` is double)

## Validation
Search.cpp compilation and diff checks passed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `057db43b0681`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.