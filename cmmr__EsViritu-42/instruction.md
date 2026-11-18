# Issue

**Title:** fix: rare no primary reads issue. reformat data-directory page.

## Description

Fix: exit gracefully in rare situation where no primary alignments are returns in third minimap2 step #41 

Minor reformat of data-directory page.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff306b94e84e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.