# Issue

**Title:** Slwu89/vfield expr

## Description

Thanks for bearing with me @mehalter, this fix now ensures the following code works, and all the existing tests still pass.  

```julia
using AlgebraicPetri

# Define some random model

sir_lpetri = LabelledPetriNet([:S, :I, :R], :inf => ((:S, :I), (:I, :I)), :rec => (:I, :R))

# Define some parameters and stuff as dictionaries

initial_concentrations = Dict(:S => 990, :I => 10, :R => 0)
model_rates = Dict(:inf => 0.001, :rec => 0.25)

# This works

du = Dict(:S=>0.0, :I=>0.0, :R=>0.0)
out = vectorfield(sir_lpetri)(du, initial_concentrations, model_rates, 0.01)

# This does not

du_expr = Dict(:S=>0.0, :I=>0.0, :R=>0.0)
out = vectorfield_expr(sir_lpetri)(du_expr, initial_concentrations, model_rates, 0.01)

# vectorfield_expr only works with LVectors from LabelledArrays, it should work with Dictionaries/Named Tuples/etc.

using LabelledArrays

du_expr = LVector(;Dict(:S=>0.0, :I=>0.0, :R=>0.0)...)
out = vectorfield_expr(sir_lpetri)(du_expr, LVector(;initial_concentrations...), LVector(;model_rates...), 0.01)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4e30ffae1fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.