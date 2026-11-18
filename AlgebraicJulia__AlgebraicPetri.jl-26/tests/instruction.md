# Issue

**Title:** Started migrating to the new UWD and @relation syntax

## Description

Started moving AlgebraicPetri to use multicospans and undirected wiring diagrams to support defining models using the simplified `@relation` macro instead of `@present` + `@program`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `959fd4b47954`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.