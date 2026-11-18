# Issue

**Title:** Add print info member function to `DiffusionGrid`

## Description

Add a function `void DiffusionGrid::PrintInfo(std::ostream)` that prints the configuration of the diffusion grid. Sample output:
```
DiffusionGrid: Nutrients
    D          = 0.833333
    decay      = 1e-05
    dx         = 12.6582
    max(dt)    <= 32.0461
    bounds     : 0 < c < 1
    domain     : [-500, 500] x [-500, 500] x [-500, 500]
    resolution : 80 x 80 x 80
    num boxes  : 512000
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3dac969a91b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.