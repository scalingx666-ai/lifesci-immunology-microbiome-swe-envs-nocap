# Issue

**Title:** Improve error message on refhash mismatch

## Description

* Reword the refhash error message to be clearer.
* Also write refhash error message to the log
* Also improve the error message on malformed FASTA header

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16d676aa0874`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.