# Issue

**Title:** Set min contig size to 2000 and warn if smaller contig is seen

## Description

We sometimes see users run Vamb with a lot of small contigs. In order to alert users that this will results in degraded binning performance, Vamb now warns users both with a runtime warning to stderr, and with a warning in the log file, if any contigs are shorter than the minimum contig size. Also, set the default minimum contig size to 2000.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d013229fd532`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.