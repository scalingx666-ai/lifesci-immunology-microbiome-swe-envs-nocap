# Issue

**Title:** Bugfix: Create out_dir/tmp in parsebam if needed

## Description

Temp files from PyCoverM are stored in out_dir/tmp/pycoverm, but the tmp directory was not created by the parsebam module. This led to a failure to make the pycoverm dir, crashing Vamb.

Fix issue #167

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `efa3e5a37646`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.