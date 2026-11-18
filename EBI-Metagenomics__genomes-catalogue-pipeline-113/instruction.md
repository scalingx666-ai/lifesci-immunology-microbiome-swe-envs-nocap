# Issue

**Title:** Feature/db update

## Description

Updates to tools and databases:

- InterProScan `5.62.94.0` -> `5.73-104.0`
- AMRFinderPlus `3.11.4 `-> `3.12.8`
- AMRFinderPlus DB `2023.02.23.1` -> `2024.01.31.1`
- run_dbCAN `4.1.2` -> `4.1.4`
- dbCAN DB `V12` -> `V13`
- Rfam `14.9` -> `15.0`
- kegg-pathway-completeness `1.0.5` -> `1.3.0`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c0c19e6aea6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.