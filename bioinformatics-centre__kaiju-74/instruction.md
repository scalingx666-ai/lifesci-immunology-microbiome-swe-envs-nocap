# Issue

**Title:** Update MarDB helper script

## Description

+ removes `HTSeq` dependency
+ supports either Python 2 or 3 (tested with 2.7 and 3.6)
+ cleans and optimizes the python code

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84d756b8d0e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.