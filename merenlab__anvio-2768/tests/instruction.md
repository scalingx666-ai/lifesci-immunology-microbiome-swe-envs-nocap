# Issue

**Title:** External structures pangenome input

## Description

`anvi-gen-structure-database` / `anvi-update-structure-database` import pre-computed structures (`--external-structures`) for the genes of a pangenome, not just a contigs-db, if you already have them or want to use a different prediction software than MODELLER and ColabFold.

Biggest change on the side of the user is an updated external-structure file which needs "genome name" and "gene caller id" in addition to the path to a structure file. The gene cluster id is discovered by anvi'o with the pan db, and the same external structure can be used by pan db made using different clustering parameters.
Internally, ExternalStructureFile becomes a source-agnostic parser/validator (detects the valid format of the external structure, file exists, etc).

And we also have associated new tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3493a884c854`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.