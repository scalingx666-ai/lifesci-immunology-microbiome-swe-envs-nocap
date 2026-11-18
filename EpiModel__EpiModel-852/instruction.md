# Issue

**Title:** On reinit, use provided params

## Description

The reinit code in EpiModel now superseeds the `reinit_msm` however, this function behavior is to copy the params from the restart point and not use the ones provided by netsim.

This PR reverts that as it is the  way we modify params for the scenario API (and even without).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f69815730adc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.