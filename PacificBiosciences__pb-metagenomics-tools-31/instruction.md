# Issue

**Title:** Bug fixes

## Description

Outputs listed in rule `tax_metagenome` were missing the `genbank` piece, one folder was numbered incorrectly. This caused the workflow to crash when the expected outputs were not found (even though the step completes successfully).

Also fixed output filename structure in rule `all`, for same reasons listed above.

Sidenote - Benchmarking showed values for `max_rss` ranged between 37-49 Gb for K51 and 51-52 Gb for K31.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71cb8e4adec0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.