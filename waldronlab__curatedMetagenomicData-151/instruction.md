# Issue

**Title:** Change deprecated datasets to defunct

## Description

Also updated the error message to be more informative when they do not have an internet connection and are unable to download data using  #`curatedMetagenomicData()` as discussed here: #150

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8d8dc36c87d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.