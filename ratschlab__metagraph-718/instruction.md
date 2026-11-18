# Issue

**Title:** Fix SSHash builds under a low file-descriptor limit

## Description

SSHash builds can abort with “cannot open file” when parallel workers exhaust the file-descriptor limit while writing temporary runs. Bound simultaneous output files using the same descriptor headroom as the merge, while keeping tuple generation and sorting parallel.

Update the SSHash submodule to include the fix and a 24-file/32-thread construction-and-lookup case. The existing MetaGraph 24-file/32-thread integration test is unchanged.

With delayed output opens, the unchanged integration test fails before the fix and passes afterward on Linux.

Prepared with Codex.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93892080e5c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.