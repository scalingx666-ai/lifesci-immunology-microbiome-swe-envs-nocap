# Issue

**Title:** Process bin quality assessemnt in parallel

## Description

Bin quality assessment in Binette was running sequentially, underutilizing CPU and becoming the main bottleneck when processing a lot of bins as mentioned in #71 .

## Added in this PR:
* Added multiprocessing with **joblib** to run bin quality assessment in parallel.
* Use sequential mode when one CPU is given or when bins count is too small to benefit from parallelism (less than 6k bins).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c481d7c1ead2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.