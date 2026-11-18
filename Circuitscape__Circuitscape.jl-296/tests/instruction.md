# Issue

**Title:** Pass the suppress_messages arg to some functions new to 5.8.0

## Description

The `csinfo()` calls in `multiple_solve()` as well as for printing the solver used did not have `cfg["suppress_messages"]` passed in as an arg. Added `suppress_messages::Bool` as an arg to `multiple_solve()` and pass it into `csinfo()` calls where the default value of `false` was previously being used.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a79911e1ea5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.