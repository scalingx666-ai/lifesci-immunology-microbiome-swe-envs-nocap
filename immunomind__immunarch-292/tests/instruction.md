# Issue

**Title:** Fix for ClustalW executable name

## Description

ClustalW executable now can be named clustalw and clustalw2 (names differ on different OS)
Fixes for formatting and styling in various files

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `11dd55bc6555`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.