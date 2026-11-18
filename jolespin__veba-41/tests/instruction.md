# Issue

**Title:** v1.4.2

## Description

* [2023.12.21] - `GTDB-Tk` changed name of archaea summary file so VEBA was not adding this to final classification. Fixed this in `classify-prokaryotic.py`.
* [2023.12.20] - Fixed files not being closed in `compile_custom_humann_database_from_annotations.py` and added options to use different annotation file formats (i.e., multilevel, header, and no header).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `237479831e04`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.