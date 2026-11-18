# Issue

**Title:** add function for arriving new nodes to the dat object

## Description

The existing `nwupdate.net` code used a combination of the `arrivals` indices and `nArrivals` (= `length(arrivals)`) when updating the `networkDynamic` object.  It appears that code would only have worked as intended when all arrivals were "new" nodes (with indices starting at the previous network size + 1 and continuing from there).  For that reason I have formalized the requirement that the arriving nodes be new nodes (rather than pre-existing nodes that are simply being re-activated) in the `arrive_nodes` function added in this PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19e933afd19e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.