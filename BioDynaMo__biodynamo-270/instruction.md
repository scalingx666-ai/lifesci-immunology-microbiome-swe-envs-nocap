# Issue

**Title:** Added version check and threshold fix for ParaView in epidemiology demo

## Description

Since ParaView 5.10 the data descriptors of the threshold object have been changed. This PR suggests a change in the rendering process of the epidemiology demo where the PV version is checked and the data descriptors are set accordingly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8762fa70c2e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.