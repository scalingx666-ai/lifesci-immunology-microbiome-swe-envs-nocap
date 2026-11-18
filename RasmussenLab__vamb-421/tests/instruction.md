# Issue

**Title:** Misc cleanup

## Description

* Do not allow hash comments in FASTA files, which do not support this normally
* Remove dead code
* Clean up help strings in argument parser
* Simplify FASTA parser and hopefully make it more robust

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7f225f3c771`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.