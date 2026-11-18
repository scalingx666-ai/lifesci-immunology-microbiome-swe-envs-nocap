# Issue

**Title:** only keep sra runs that were asked about

## Description

Turns out when you ask SRA for a run's metadata, you actually get back information about all runs for the associated experiment (SRX...). So you get an unexpected list of many more accessions prior to starting the workflow or whatever you want to do with these.

The fix is simple, make sure the resulting table only contains entries matching what the user provided.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `14c11b131526`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.