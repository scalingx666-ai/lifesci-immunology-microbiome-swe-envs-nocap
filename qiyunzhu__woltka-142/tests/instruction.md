# Issue

**Title:** Optimized ordinal mapper using binarized data structure

## Description

This is the final result of my efforts in optimizing the ordinal mapper, highlighting significantly reduced memory usage (more than 40% decrease), and slightly reduced runtime (nearly 10% decrease).

In this new solution, multiple pieces of information are store in a single integer, instead of a tuple of multiple variables. Because Python has notable overhead in creating variables (which are objects), this change dramatically saved the memory consumption, therefore allowing the program to handle much larger databases.

The read / write of the information is achieved by **bitwise operations**, which are efficient. This also opens new possibility of using Cython for further improvement of performance.

In addition, multiple parts of the ordinal mapping feature have been optimized to maximize performance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3bb99f55e9d3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.