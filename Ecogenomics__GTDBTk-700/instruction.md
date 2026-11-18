# Issue

**Title:** 2.7.1

## Description

*April 17, 2026*

Bug Fixes:

* #699 
     - Although all genomes are classified with `skani`, selecting `--place_species` still requires `_bac_gids`, `_ar_gids`, and `bac_ar_diff` for downstream processing.
* #698 
    - Fixes an MD5 mismatch in the `check_install` configuration.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `443274667ffc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.