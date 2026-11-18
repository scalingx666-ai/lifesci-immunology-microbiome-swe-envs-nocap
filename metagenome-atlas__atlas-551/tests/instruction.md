# Issue

**Title:** GTDB-tk requires rule `extract_gtdb` to run first

## Description

The GTDB-data download was split into two rules with commit 591446d181d6620efc79e83649d7a7865bbdd415
1. Download (rule `download_gtdb`)
2. Unpackung of archive (rule `extract_gtdb`)

The rule `identify` now needs to depend on the output of the unpacking step.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e9dbc5d6bb6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.