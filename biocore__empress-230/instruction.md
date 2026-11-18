# Issue

**Title:** Empress tests

## Description

This PR addresses the empress tests in #142. Since test-empress.js is already a large file, I decided to upload this first to make reviewing a bit easy. This PR also fixes a bug that caused the root node to always get a black node. (I thought there was an issue for this but I couldn't find it).

Also getCoords, addTriangleCoords, addThickVerticalLineCoords, and thickenSameSampleLines do not have tests because there operations will be moved to the vertex shader in #190 and #214.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a556eb8d732d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.