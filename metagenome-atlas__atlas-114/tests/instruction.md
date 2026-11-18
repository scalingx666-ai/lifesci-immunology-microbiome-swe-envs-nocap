# Issue

**Title:** Spades 3.12

## Description

Ads spades 3.12, which handles merged reads separately.
Added "loose parameters"
add options to individually toggle:
- normalization
- error_correction
- merging 
- error_correction of spades (BaysHammer), 
- filtering of contigs

added pythonic symlinks to reduce memory storage.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9be388f6d38c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.