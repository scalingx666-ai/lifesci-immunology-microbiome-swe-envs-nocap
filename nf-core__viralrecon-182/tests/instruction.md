# Issue

**Title:** Default to using --callers bcftools for --protocol metagenomic and --callers ivar for --protocol amplicon

## Description

This is mainly because iVar doesn't have a clever way of dealing with strand biases that are typical for amplicon data (see ).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5013c61324a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.