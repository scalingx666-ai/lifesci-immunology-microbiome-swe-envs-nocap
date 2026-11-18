# Issue

**Title:** Do not canonicalize `+` and `-` during ODESystem conversion

## Description

PR:
```julia
julia> ModelingToolkit.equations(model_odesys)
2-element Vector{Equation}:
 Differential(t)(A1(t)) ~ (2A1_A1*(A1(t)^2) + A1_A2*A1(t)*A2(t) + A2_A1*A1(t)*A2(t)) - (2A1_A1*(A1(t)^2) + A1_A2*A1(t)*A2(t) + A2_A1*A1(t)*A2(t))
 Differential(t)(A2(t)) ~ (2A2_A2*(A2(t)^2) + A1_A2*A1(t)*A2(t) + A2_A1*A1(t)*A2(t)) - (2A2_A2*(A2(t)^2) + A1_A2*A1(t)*A2(t) + A2_A1*A1(t)*A2(t))
```

Master:
```julia
julia> ModelingToolkit.equations(ODESystem(model_bilayer))
2-element Vector{Equation}:
 Differential(t)(A1(t)) ~ 0
 Differential(t)(A2(t)) ~ 0
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a9d655fc101`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.