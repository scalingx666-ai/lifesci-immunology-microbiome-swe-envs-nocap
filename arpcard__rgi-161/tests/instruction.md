# Issue

**Title:** Make hardcoded paths configurable via environment variables

## Description

DB_PATH will override script_path/_db/
DATA_PATH will override script_path/_data/

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2cb7238181b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.