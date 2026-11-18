# Issue

**Title:** Update database paths and a few configs

## Description

Went down a rabbit hole to change all paths generated in VIRify... I could have saved some of these by changing the configs alone, but since I was here 😅️ A summary:

- Moved `pprmetaGet` to `get_db`
- Removed all `databases` instances from path generators
- Adapted `download_databases` accordingly
- Behaviour tested with MGnify configs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f2bd66508bf2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.