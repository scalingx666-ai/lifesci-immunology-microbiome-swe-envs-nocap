# Issue

**Title:** Sample medoids faster and more thoroughly

## Description

Before, medoids were sampled with random.choices, which chooses with replacement, leading to unnecessary duplicate work checking medoids that were already found to be poor. Change this to random.sample.
Also, keep a list of tried medoids through the entire wander_medoid function call, so even when the medoid shifts, poor medoids from previous iterations are not retried.
Also, when picking the maxsteps number of medoids to try, automatically exclude the medoids already checked.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f8b875f6fdea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.