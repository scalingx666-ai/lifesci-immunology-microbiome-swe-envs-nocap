# Issue

**Title:** Improve error message on mismatching refhash

## Description

Mismatching identifiers in FASTA and BAM files has caused a lot of issues for our users. This is what the mechanism of refhashing was intended to detect and prevent.
However, the error on a mismatching refhash is not that friendly, in that it only shows the hash, but not the identifiers that caused the hash. Improve the error message by showing the first mismatching identifier.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `311f22b4deea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.