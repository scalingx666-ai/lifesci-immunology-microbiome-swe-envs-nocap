# Issue

**Title:** MIN Fix errors/warnings with RefSeqInfoVector C code

## Description

This seems to be causing problems in https://gitlab.com/ngless/ngless/-/jobs/122904272

Newer versions of GCC being strict about `void*` it seems.

I'm not familiar with Haskell <-> C++ so please review.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c33ea0ecb7bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.