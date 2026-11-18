# Issue

**Title:** Add CORD-19 resource to workflow and build script

## Description

This follows up on #941 so that the script to generate CORD-19 statistics and figures is run daily.  It also tests that the statistics are available in the manuscript.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `016a5642ec32`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.