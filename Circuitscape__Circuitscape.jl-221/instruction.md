# Issue

**Title:** Vl/travis - dependency stuff

## Description

1. Updated travis.yml to use Julia 1.3 since that's Circuitscape's dep in the [Project.toml](https://github.com/Circuitscape/Circuitscape.jl/blob/master/Project.toml#L28). I thought this might solve the failure occurring in Travis, but I'm not sure since Appveyor has been passing. 

2. I also added testing directly on osx to the travis.yml. 

3. I updated the compat section in Project.toml to use [preferred formatting](https://docs.julialang.org/en/v1.0/stdlib/Pkg/#Caret-specifiers-1)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5da6757e1749`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.