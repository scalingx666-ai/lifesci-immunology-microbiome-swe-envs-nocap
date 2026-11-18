# Issue

**Title:** Pass qualityType through to ShortRead

## Description

Creates a `qualityType` argument to all exported functions which call (directly or indirectly) `ShortRead::readFastq()`.  Most of these are via `ShortRead::yield()`.  This addresses #682, in which PacBio CCS reads with uniformly high quality (>25 for the first 10000 bases in the file) are incorrectly assumed to be using the Solexa-format for fastq quality scores.

Passes `R CMD check` on my machine, except for notes that come from the official version, and seems to work correctly in my own PacBio amplicon analysis.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c4e8a2d57fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.