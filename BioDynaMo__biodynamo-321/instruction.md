# Issue

**Title:** Fix discretization offsets in DG

## Description

This PR targets issue #311. In this PR, we shift the ParaView export by half a box length. Effectively, this means we change the discretization points from the top left, to the center of the boxes. See below form `x -> o`. We additionally change the initializers for the `DiffusionGrid` because these need to be evaluated at the new discretization points. Two tests needed to be modified in this process as well. 

```
x-----------x-----------x------------
|           |           |           |
|     o     |     o     |     o     |
|           |           |           |
-------------------------------------
x-----------x-----------x------------
|           |           |           |
|     o     |     o     |     o     |
|           |           |           |
-------------------------------------
x-----------x-----------x------------
|           |           |           |
|     o     |     o     |     o     |
|           |           |           |
-------------------------------------
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f466ff33324`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.