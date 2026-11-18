# Issue

**Title:** Add view translate_join, index now stores original sequences

## Description

* Index now stores the original sequences and not the translated sequences
* Index does not store sequence lengths anymore, they get calculated from the original sequences when needed
* Added view_translate_join
* Fix setting of thread number for search and index
* Updated submodules

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b41d68715a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.