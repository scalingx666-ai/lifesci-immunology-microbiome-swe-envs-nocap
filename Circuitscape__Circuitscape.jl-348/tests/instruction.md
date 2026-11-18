# Issue

**Title:** Make assertion check consistent with iterativesolvers.jl

## Description

Should not normalize by the lhs, but by the rhs instead, like in IterativeSolvers.jl. Also use L2 norm like in IterativeSolvers.jl

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e9861d3574a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.