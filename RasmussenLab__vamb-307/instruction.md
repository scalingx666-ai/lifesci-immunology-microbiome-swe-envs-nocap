# Issue

**Title:** Do not make files lengths.npz and contignames

## Description

These files are redundant w.r.t. composition.npz. Although it takes more memory to load the latter, it's unlikely that storing the composition briefly is going to be a problem, since if it was, Vamb would cause OOM elsewhere anyway.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67e9b706d070`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.