# Issue

**Title:** Fix RuntimeError (issue #165)

## Description

I've been encountering the same Runtime Error as was mentioned in  using RGI main since August 2024. 
This quick PR seems to resolve it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d00399efdcf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.