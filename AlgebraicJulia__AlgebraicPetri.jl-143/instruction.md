# Issue

**Title:** Changed `prim_petri` to fix issue when type system has multiple states.

## Description

This change attempts to address an issue with `prim_petri`. It appears the states of the type system (`s_map`) were not being determined correctly. It did not arise as an issue before because most examples use a type system with only a single state, but in recent examples with multiple type states, the typing has been incorrect.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c89c621454c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.