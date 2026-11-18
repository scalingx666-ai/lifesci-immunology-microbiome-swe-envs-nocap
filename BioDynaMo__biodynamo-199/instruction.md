# Issue

**Title:** BugFix for Diffusion Grid Initialization

## Description

![hybrid_snapshot_1](https://user-images.githubusercontent.com/44771875/128075698-b0e6f0ff-a990-410c-aaf3-5ec43c585ad9.png)
The Initialization of the diffusion grid only set the values of one of the two grids while the others remained zero. After the first iteration, we swap the arrays and artificially created zero boundaries resulting in very strange boundary effects. This PR fixes the initialization.
Image was obtained when running the diffusion `EulerGrid` with closed boudaries and inital condition `SetValues(){return 0.5;}`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d90157b95f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.