# Issue

**Title:** fix default DB env var name

## Description

Hello, 

there is a typo in `metaphlan/utils/create_toy_database.py` environment variable for DB location must be `METAPHLAN_DB_DIR` instead of `DEFAULT_DB_FOLDER`

last one is an internal metaphlan python variable

regards

Eric

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7558cd931aab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.