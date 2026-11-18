# Issue

**Title:** Fix translated search alignment issue

## Description

Add a new search-type 4 for special case of returning nucleotide backtrace for transnucl-transnucl search in offsetalignment, revert convertalis

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31f6d7ac3c8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.