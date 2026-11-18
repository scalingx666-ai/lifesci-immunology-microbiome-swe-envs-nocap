# Issue

**Title:** ENH+TST Expand subfeatures when counting with a GFF file

## Description

Using a GFF containing `"gene_name=nameA,nameB"` would result in:

    nameA,nameB    1

Now the same results in:

    nameA    1
    nameB    1

This follows after https://git.io/vpagq and the case of:

    Parent=AF2312,AB2812,abc-3

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8459d7eb21a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.