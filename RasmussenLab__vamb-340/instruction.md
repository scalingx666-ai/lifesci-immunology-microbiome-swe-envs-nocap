# Issue

**Title:** Rewrite reclustering

## Description

This PR completely rewrites reclustering. A few important differences:
* It now uses Markers from vamb.parsemarkers, avoiding shelling out to prodigal
  and hmmer
* The algorithm used to pick the best disjoint bins in the DBScan algorithm is
  faster, and should also produce better results.
* The code is almost completely statically analyzable
* Pandas is no longer used

It also refactors `parsemarkers.py`.
It is built on #339, so that needs to be merged first.

## TODO
- [x] Merge #339 
- [ ] Add tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f273967877d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.