# Issue

**Title:** add @jmeppley download fixes to dev branch

## Description

Based on 
Fixes 

Thanks @jmeppley

- [x] Test downloads `aviary configure --download gtdb eggnog singlem checkm2 metabuli --gtdb-path ~/db/test/gtdb --checkm2-db-path ~/db/test/checkm2 --eggnog-db-path ~/db/test/eggnog --singlem-metapackage-path ~/db/test/singlem --metabuli-db-path ~/db/test/metabuli`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `657d966ff440`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.