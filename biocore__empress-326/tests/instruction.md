# Issue

**Title:** PERF: Speed-up taxonomic string preprocessing

## Description

The string operations are vectorized which makes processing the EMP
taxonomy strings go from 45 seconds to ~1.5 seconds.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b73e5825b5f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.