# Issue

**Title:** [MRG] remove unnecessary bcalm_unitigs cli arg

## Description

While working on #430 I realized that `spacegraphcats/cdbg/bcalm_to_gxt.py` still took an argument `bcalm_unitigs` that it did not, in fact, need or use. This PR removes it from the argument parsing as well as the Snakefile.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e1310748677a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.