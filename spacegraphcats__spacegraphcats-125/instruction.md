# Issue

**Title:** Better checkpoint saving and loading

## Description

The checkpoint saves are threaded and zipped (re #115).  The loads are now compatible with disconnected graphs (re #112).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca6f21c46669`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.