# Issue

**Title:** fix: find fastqc dependency for trim-repetitive

## Description

FastQC is required for the trim-repetitive option, but might not be found if fastqc-start is not also run.  Simple fix is to always search for the dependency if trim-repetitive is specified.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab97268b270d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.