# Issue

**Title:** fix non-deterministic protein id for pangenome

## Description

Small fix after #2766.
Protein id were non deterministic and break when you split `anvi-gen-structure-database` with the flags `--only-msa/--only-predict`.
Now is good :D

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a875e0ffc708`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.