# Issue

**Title:** Drop the SuiteSparse dependency and add stdlib compat entries

## Description

- Remove `SuiteSparse` from the dependencies. On Julia 1.12 it is a compatibility shim whose `CHOLMOD` module is `SparseArrays.CHOLMOD`; the package used it in one method signature, now written as `SparseArrays.CHOLMOD.Factor`.
- Add `[compat]` entries for the stdlibs `Dates`, `LinearAlgebra`, `Logging` and `SparseArrays`.

Full test suite passes locally (6 suites, 4 threads).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26521a966c3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.