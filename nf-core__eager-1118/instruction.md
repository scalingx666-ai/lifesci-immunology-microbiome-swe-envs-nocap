# Issue

**Title:** check params.bamfiltering_savefilteredbams for bai

## Description

Fix #968 
SAMTOOLS_LENGTH_FILTER_INDEX|SAMTOOLS_FILTER_INDEX published indexes without checking params.bamfiltering_savefilteredbams

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff31e25df278`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.