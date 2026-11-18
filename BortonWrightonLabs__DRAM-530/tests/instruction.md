# Issue

**Title:** fix: decouple SUMMARIZE from ANNOTATE output through QC for annotations

## Description

SUMMARIZE was reliant on ANNOTATIONS output directly, through the access of ANNOTATE.out.ch_trna_combined (from QC), meaning --annotations failed. Now these are decoupled, but QC still outputs to the ANNOTATE output namespace.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45947355343e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.