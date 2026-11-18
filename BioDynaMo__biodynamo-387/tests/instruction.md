# Issue

**Title:** Change FetchContent_Populate to FetchContent_MakeAvailable

## Description

According to #386, since FetchContent_Populate is deprecated we need to get rid of it. This PR makes this possible replacing it with the function `FetchContent_MakeAvailable`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8bb6b7ab254`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.