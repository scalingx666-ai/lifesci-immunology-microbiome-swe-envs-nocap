# Issue

**Title:** Add internal function to use in Omniscape

## Description

This PR adds a function to Circuitscape's internals that can be used to call other Circuitscape internals to compute the current flow for Omniscape moving window iterations.

Prior to this change, I had this function written in the Omniscape code base, but that required the assumption that certain Circuitscape internals would not change. But given that internals can change even with minor or patch releases, I figured it would be more reliable to have this function internal to Circuitscape so it can be tested prior to Circuitscape release, rather than discovering breaking changes in Omniscape down stream.

I added a test to test/Internals.jl for the function I added, and it really just tests for syntax/correct inputs (since the other Circuitscape tests already check for correctness).

I've already updated Omniscape to use this function and tested it (with success!), so this should be good to merge immediately.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `327243b34dfb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.