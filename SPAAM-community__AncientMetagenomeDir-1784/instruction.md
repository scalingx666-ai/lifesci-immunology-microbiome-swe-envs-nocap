# Issue

**Title:** Add NR for samples without recorded radio-carbon material

## Description

Amdirt's `validate` command checks the entries of the column `sample_material` in the `dates.tsv` against the values against `assets/enums/material.json`. The case that the material used for the radio carbon analysis has been recorded is not escaped so far.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a390202e2f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.