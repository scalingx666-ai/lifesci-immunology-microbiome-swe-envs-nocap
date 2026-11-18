# Issue

**Title:** 196 implement odr summary tab in html report

## Description

- Update Interactive Report to give the Summary of the entire run
- Separate tass cutoff by sample type to avoid the high prob. false positives in certain types
- Adding histogram sparkplot to the summary table
- Adding direct links to other tabs first pass from another tab
- Update some docs in the report html

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b090a45ec0f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.