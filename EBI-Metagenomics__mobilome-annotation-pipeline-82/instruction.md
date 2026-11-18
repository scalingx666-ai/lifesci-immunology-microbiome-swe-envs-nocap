# Issue

**Title:** Only run IntegronFinder for contigs > 100kb

## Description

This change is two-fold:
- Bug fix -  (attempting to work around this)
- Performance improvement - This tool creates a large number of folders and files (one folder per contig, plus several files within each). This is problematic for metagenomes. After discussing with @Ales-ibt, we decided to run this tool only on the largest contigs to mitigate this issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ead8bf2c4f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.