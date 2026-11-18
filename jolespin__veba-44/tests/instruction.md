# Issue

**Title:** blacklist eukaryotes

## Description

* [2023.12.28] - Added `--blacklist` option to `compile_eukaryotic_classifications.py` with a default value of `species:uncultured eukaryote` in `classify_eukaryotic.py`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ed29105ff34`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.