# Issue

**Title:** Add command to extract Neff scores for MSA

## Description

As discussed in #638, this code adds a new command to output Neff scores. The command is called `profile2neff`. It takes a profile database as input and outputs per-residue Neff scores for a query sequence.

The scores are written to a `DBWriter` that then contains two lines for each sequence: a header similar to `profile2pssm`'s output and a line containing tab-separated Neff scores (from the range [1;255]) for each residue. The score is converted from the internal float representation to char using the `convertNeffToChar` function from `MathUtil.h`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed4c55fa21c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.