# Issue

**Title:** refactor(mmseqs): Remove desc db in favor of direct mmseqs theader use

## Description

mmseqs covertalis can return the target header as the descriptions instead of relying on the sqlite description database. This is more foolproof since any database update can directly pull from the new headers. When we build the new kegg database, we can build it with updated headers from the kff files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `778421a376bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.