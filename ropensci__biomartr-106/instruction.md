# Issue

**Title:** Fixed bug for ensembl ftp base url path for windows

## Description

A bug for windows, ensembl paths did not work at all, since file.path function removes trailing slashes there.
It now uses paste0, which is consistent on all OS. 
I also bumped version, so you can push this version to cran.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00d263b3e571`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.