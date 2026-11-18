# Issue

**Title:** Enhance usability for large, diverse input

## Description

This PR makes CATCH more accessible to users via a single command and/or in case users overlook options that specifically enhance its runtime and memory usage.

Specific goals are:

- Make `design_large.py`, which wraps `design.py`, and:
  - Specifies, by default, the locality-sensitive hashing options (namely, `--filter-with-lsh-minhash`) that specifically enhance runtime and memory usage, often with considerable impact
  - Specifies, by default, the sequence clustering options that also enhance runtime and memory usage
- Parallelize design across separate clusters or input taxa automatically, i.e., without requiring separate commands by the user
- Reduce memory usage for sequence clustering
- Add, to the README, reasonable suggested values for locality-sensitive hashing options that affect runtime and additional information currently in the `--help` messages
- Emphasize that `design.py`, using its cautious defaults, are for single taxa or other smaller datasets, and clarify text throughout the README regarding different manners of running CATCH and recommended options

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f363cb3940d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.