# Issue

**Title:** Fix download of databases and also fixed pixi 0.71+ issues

## Description

# Changes
- Fixed aviary configure --download failing with "both long_reads and short_reads_1 are set to none" by adding download_databases to SUBCOMMANDS_WITHOUT_READS in processor.py.
- Fixed CI breaking under pixi 0.71, which broke the old system-requirements CUDA setup and stripped linux-64 from every environment.
- Migrated GPU CUDA to pixi rich-platforms using a dependency-free cpu anchor feature, pinned pixi >=0.71, and regenerated the lock to v7.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `396a742b4f6b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.