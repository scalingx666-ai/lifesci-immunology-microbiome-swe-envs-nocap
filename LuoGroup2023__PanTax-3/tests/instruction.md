# Issue

**Title:** estimate abundance with GAF file, no longer json file

## Description

+ estimate abundance with GAF file, no longer json file.
+ fix the bug when using GAF file to estimate abundance.
In the GAF file, the `read_end` columns may be `*` instead of a number.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34ce1b4b4c51`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.