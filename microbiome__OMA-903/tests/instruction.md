# Issue

**Title:** Fix ML chapter build

## Description

Alpha diversity metrics are already in assay() after preprocessing. If alpha diversities are specified again in run_ml(), they are two times in the data. The newer version of dplyr inside mikropml fails.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5cab63b1fd8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.