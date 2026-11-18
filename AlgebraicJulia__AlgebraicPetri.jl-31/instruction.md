# Issue

**Title:** Resolve method ambiguity with ACSet constructors

## Description

AlgebraicPetri is currently broken on Catlab master due to a method ambiguity with [this constructor](https://github.com/AlgebraicJulia/Catlab.jl/blob/6d14c7546734e982f5392cfd0f6fa397a05b700a/src/categorical_algebra/CSetDataStructures.jl#L58). This PR slightly tightens the types of the constructors for Petri nets, labelled Petri nets, etc.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6829a69a640`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.