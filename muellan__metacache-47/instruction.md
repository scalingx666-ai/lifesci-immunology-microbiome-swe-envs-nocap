# Issue

**Title:** Avoid command line too long error when globbing genome files

## Description

While running `metacache-build-refseq small` I got an error after downloading all of bacteria, because doing `*.gz` leads to a command line too long on my system.

This should fix it. Note, I added parallelization.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d5b1cdd91672`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.