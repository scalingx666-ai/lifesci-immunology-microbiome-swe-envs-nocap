# Issue

**Title:** patch for data race

## Description

Data race occurs when a read maps to multiple graphs and read needs to be reverse complemented in each Go routine. This PR fixes that and also adds a flag to skip exact alignments during the align subcommand, leaving only approximate mappings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45269468dae3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.