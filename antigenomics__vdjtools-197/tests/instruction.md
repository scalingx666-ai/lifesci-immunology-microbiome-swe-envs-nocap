# Issue

**Title:** Release 5.0.2: preserve AIRR identifier strings

## Description

AIRR identifier columns such as `sequence_id=001` were converted to floating-point measurements and could be averaged during clonotype collapsing. Keep `*_id` values as strings with first non-null representative aggregation; retain numeric measurement aggregation such as `v_identity`.

Validation: the identifier regression failed before the fix; all 13 IO tests, Ruff, diff checks and the warning-free Sphinx build pass. Version 5.0.2 supplies the identifier contract needed by mirpy's new embedding tables.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `633e90b5b20a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.