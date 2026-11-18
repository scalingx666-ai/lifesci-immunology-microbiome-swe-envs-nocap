# Issue

**Title:** geNomad, IntegronFinder2, ISEScan version update

## Description

Updated tools:
geNomad v1.6.1 -> v1.11.1
geNomad db -> v1.9
IntegronFinder2 v2.0.2 -> v2.0.6
ISEScan v1.7.2.3 -> v1.7.3

The IntegronFinder parser script was modified to correctly handle header skipping in different output versions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cacf51df8692`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.