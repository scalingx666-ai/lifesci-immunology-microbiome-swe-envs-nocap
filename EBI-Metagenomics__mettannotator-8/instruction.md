# Issue

**Title:** Bugfix/escaped character handling

## Description

Cleaned up uniFIRE scripts, renamed them and fixed how the escaped characters from uniFIRE are handled by [convert_cds_into_multiple_lines.py](https://github.com/EBI-Metagenomics/mettannotator/blob/bugfix/escaped-character-handling/bin/convert_cds_into_multiple_lines.py)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e91f1af44a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.