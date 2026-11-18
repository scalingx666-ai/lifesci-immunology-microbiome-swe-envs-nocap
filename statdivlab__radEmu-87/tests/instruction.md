# Issue

**Title:** Add option to bypass error about having categories with only zero counts

## Description

Add optional argument `unobserved_taxon_error` to `emuFit()` that is `TRUE` by default. When `TRUE`, `emuFit()` will throw an error if a column of `Y` is made up of all zero values. When `unobserved_taxon_error = FALSE`, this error will be bypassed and `emuFit()` will run in these settings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72fa58baeac3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.