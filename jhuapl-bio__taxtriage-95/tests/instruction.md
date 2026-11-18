# Issue

**Title:** fixing minimum mapq for filtering host

## Description

- Added fix for host removal not properly passing the output due to minmapq global variable usage

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3718f2cf6aa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.