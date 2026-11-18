# Issue

**Title:** Allow `vectorfield_expr` work with more types

## Description

Originally was trying to drop `labelled_arrays` from AlgebraicPetri's dependencies, but it turns out DifferentialEquations.jl doesn't support dictionaries of initial conditions... so I suppose we are stuck with this as a dependency if we want to have named results. One thing that this did allow was for us to generalize our `vectorfield` functions a bit. While DifferentialEquations.jl maybe doesn't support it, it's good for our functions to be as general as they can be.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `085efac06d3b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.