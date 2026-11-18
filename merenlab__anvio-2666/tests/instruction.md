# Issue

**Title:** Reaction network FormulaMatcher match by charge in addition to formula

## Description

It is important to be able to match a chemical formula to compounds in a reaction network taking into account the charge.

@ivagljiva, I now see you made an equivalent change to this in branch [`compound_matching`](https://github.com/merenlab/anvio/tree/compound_matching), so feel free to delete it :)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c224e0e85b4f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.