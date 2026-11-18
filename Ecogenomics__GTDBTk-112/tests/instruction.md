# Issue

**Title:** Prodigal input checking, exit conditions, and --force

## Description

Checks to see if input files are empty before gene calling.
Checks to see if any genes were actually called.
Exit from prodigal if an error is encountered on any genome (unless --force is specified).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3eaa4c57865`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.