# Issue

**Title:** Debug/gff writer

## Description

Fix on `parse_viral_pred.py` script to avoid reporting prophage contigs in high- or low- confidence outputs, yielding duplicate predictions in the final gff file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf2af71ff962`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.