# Issue

**Title:** Add --bamdir CLI argument

## Description

The previous --bamfiles argument is un-ergonomic in the presence of many BAM files. While the user can pass a glob, e.g. `bams/*`, this is expanded in the shell, such that Python itself gets an argument for each BAM file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24bab51e2983`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.