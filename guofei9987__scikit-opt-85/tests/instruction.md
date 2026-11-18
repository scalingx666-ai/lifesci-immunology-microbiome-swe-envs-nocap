# Issue

**Title:** Add verbose and precision for PSO

## Description

Add verbose and precision parameters for PSO

If verbose is True, it will print the simple result of each iter.

If precision is None, it is the same with original
If precision is a float, the loop will stop if the difference between pbests is less than precision (continuous N number)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e001e41d291a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.