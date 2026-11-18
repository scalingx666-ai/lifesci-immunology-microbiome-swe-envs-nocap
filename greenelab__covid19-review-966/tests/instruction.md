# Issue

**Title:** Modify CORD-19 script to exit with 0

## Description

The external resources build [is failing](https://github.com/greenelab/covid19-review/runs/2625662310?check_suite_focus=true) because `CORD-19/generate-cord19-stats.sh` exits with 1.  This should allow it to ignore missing files and still exit with 0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a286bd7bfad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.