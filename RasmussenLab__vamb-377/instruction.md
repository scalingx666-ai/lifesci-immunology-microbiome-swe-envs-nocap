# Issue

**Title:** Use the correct binsplitter in TaxVamb

## Description

Previously, TaxVamb incorrectly used the inert splitter instead of the one specified on command-line, when loading its composition. Since the binsplitter is properly initialized in `calc_tnf`, such that it will not attempt to binsplit on 'C' if this separator is not present, the use of an inert splitter skipped this initialization.
This caused a bug where the lack of a separator was not detected until the data was clustered, far too late.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95f11550068c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.