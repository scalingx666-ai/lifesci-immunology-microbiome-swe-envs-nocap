# Issue

**Title:** 103 GitHub pages for multi run analysis

## Description

Adds the ability to create a multi-run analysis html file at:

`report/all.comparison.report.html` after each run. This formatting comes pre-loaded with the data for all the samples in a given run, and is the same functionality as the GH pages

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e25ddc452190`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.