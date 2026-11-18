# Issue

**Title:** Mag mapping

## Description

Added new features to `HiFi-MAG-Pipeline`:
- Use local version of CheckM2 database, rather than rely on automated download in workflow. Fixes issues previously raised.
- Added new mapping feature. Converts existing bam to paf, then filters based on unique reads, percent read aligned, and percent identity. Performs at contig and MAG level, generates a table and figure of percent reads mapped.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f62d8f4e5d66`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.