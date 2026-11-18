# Issue

**Title:** Match analysis process became 200X faster in Windows OS

## Description

- Fixed a bug in remainConsecutiveMatches
  - It will change results slightly due to corrected score calculation.
- Previously, a graph that connects consecutive matches is constructed first, and the graph is traversed to find the best combination of matches. Now, the optimal match combination is found directly. It is the main point of speeding up.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d04cb7328637`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.