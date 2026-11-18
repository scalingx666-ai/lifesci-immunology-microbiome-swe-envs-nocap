# Issue

**Title:** Experiments in exploring the taxonomy of contaminants.

## Description

- [x] add tests for load/save contam
- [ ] figure out what's going on with filter_ranks and massive counts
- [ ] integrate into reporting/snakefile

TODO thoughts:

- do we want to keep all counts, including non-contam? might let us estimate significance.
- store scaled, and maybe ksize, in contam_json. OR make a more generic run_info.json, or something.
- explore ways to select subset of contam counts. top 20? top 95%? hard threshold? some combination?

ref

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f2f81213c25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.