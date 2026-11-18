# Issue

**Title:** Conditional usage of IQTree or FastTree

## Description

For more than 2000 sequences, FastTree will be used. IQTree tree computation
is too heavy for more than 2k sequences.

I **haven't** teste this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `64cce0e87047`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.