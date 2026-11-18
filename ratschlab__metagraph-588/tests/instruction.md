# Issue

**Title:** changed default query mode: report hits with num k-mer matches

## Description

Set default query mode to `--query-mode matches`

Now, instead of just a list of labels, it returns the number of k-mer matches per label by default

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70badac40089`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.