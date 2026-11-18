# Issue

**Title:** fix: Update sambamba>=1.0.1

## Description

As described previously in #750, I suggest to update sambama.

This fixe this error `ValueError: invalid literal for int() with base 10: ' sambamba [command] [args...]'` in rule `combine_contig_stats` and rule `pileup_contigs_sample`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81d03f1b0ffd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.