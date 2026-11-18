# Issue

**Title:** Fix/mobilome compressed

## Description

GFF files are now compressed, the script was updated to deal with it and to produce a compressed header-only file when empty mobilome gffs are detected.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7be32af53b96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.