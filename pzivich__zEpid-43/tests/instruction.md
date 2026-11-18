# Issue

**Title:** Improvements to calc module

## Description

Here's the code for #42, and it has some more changes: 

 - replace `math` with `numpy`
 - abstracting some checks that are common across all the tests

One nice thing about the original #42 changes is that it maintains backwards compatibility too, eg: `results[0] == results.point_estimate`, ie you can still index like you did before.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38882047e75c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.