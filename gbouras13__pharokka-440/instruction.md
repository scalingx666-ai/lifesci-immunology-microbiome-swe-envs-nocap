# Issue

**Title:** Add protocols paper citation and bump version to 1.10.2

## Description

pharokka run --citation and the end-of-run summary now also print the Pharokka/Phold/Phynteny protocols paper alongside the existing Pharokka citation. Also fixes a duplicated "Vreugde S." author name in the protocols paper citation in the README and docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b903c0debef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.