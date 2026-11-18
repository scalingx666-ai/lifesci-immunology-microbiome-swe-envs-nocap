# Issue

**Title:** Add useful error when passed < 2 sequences

## Description

This causes various errors in either the normalization when creating the data loader, or during training, as PyTorch treats singleton dimensions differently.
When Vamb is run from command line, throw an error early after parsing contigs, and when using the tool as a package, also throw it before training.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67e9b706d070`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.