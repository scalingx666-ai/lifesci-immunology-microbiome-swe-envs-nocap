# Issue

**Title:** Further QMAX fixes and NULL initialization

## Description

I propagated through some more QMAX changes (mostly cosmetic).

There is also an added functionality, an err=NULL can be passed to the
dada(…) function if selfConsist=TRUE, in which case the maximum possile
error rates are estimated from the data as an initialization.

This corresponds to placing all sequences in one partition, as
described in the DADA1 paper (Rosen et al 2012).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae8fde7bff87`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.