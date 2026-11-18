# Issue

**Title:** Add --no-same-owner to nanopore UNTAR on Azure Batch

## Description

The nanopore Nextclade dataset untar (plain `UNTAR`) and Kraken2 DB untar (`UNTAR_KRAKEN2_DB`) lacked the `--no-same-owner` tar flag that the illumina path already applies via the `UNTAR_.*` selector. On Azure Batch, tar runs as root on a mount that does not support chown and fails restoring the archive's stored ownership.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77511804198c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.