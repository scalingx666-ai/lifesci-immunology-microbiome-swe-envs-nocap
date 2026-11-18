# Issue

**Title:** Fix TIGRFAM_HMMS and PFAM_HMM_DIR paths

## Description

`MARKER_DIR` already includes `GENERIC_PATH`. When the `GENERIC_PATH` is a symbolic link, `os.path.join` does not merge the two paths, and causes a file not found error.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7a8481b6f75`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.