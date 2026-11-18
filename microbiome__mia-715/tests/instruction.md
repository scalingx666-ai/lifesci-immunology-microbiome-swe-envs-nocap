# Issue

**Title:** Add pseudocount as method

## Description

Sometimes it might be useful to add pseudocount without other transformation (e.g. if additional transformation is applied afterwards). 

This PR adds option to add only pseudocount by using `transformAssay()`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b6ce6bf07a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.