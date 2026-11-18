# Issue

**Title:** Fix yet another inclusion problem, this time caused by a bad cDBG calculation.

## Description

Also, put in visual warnings when this happens again.

Also, add `gxt_to_gml.py`

- [x] Does this PR change the contracted DBG, catlas, or minhash DB formats?
      If so, merge with care as this will require rebuilding some big files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf3abb4736a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.