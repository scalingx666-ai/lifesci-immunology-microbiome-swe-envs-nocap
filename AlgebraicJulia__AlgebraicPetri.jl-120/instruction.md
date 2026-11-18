# Issue

**Title:** Property Petri Nets

## Description

### TODO

- [x] Finalize implementation and make sure all the cases are covered
- [x] Add testing
- [x] ~Split up `src/AlgebraicPetri.jl` This one file is getting unruly at this point and this seems like a good point to just refactor the types of petri nets into their own files~ punt on this to another PR

The main goal of this PR is to add support for Petri Nets with arbitrary metadata added to them. This also cleans up some of our types and generalizes a lot of our functions to make sure that they work on all types of petri net acsets.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f40befc229d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.