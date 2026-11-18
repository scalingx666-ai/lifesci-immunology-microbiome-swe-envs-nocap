# Issue

**Title:** Force weak_id to be a reasonable value when cluster_unoise (0.9)

## Description

Now it really ignores the `--id` param. I think that `opt_weak_id=0.9` for UNOISE is a reasonable choice. Related to #283 and https://groups.google.com/d/msg/vsearch-forum/ws7NEP68gO8/DZX6zT16BAAJ

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97c892455f70`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.