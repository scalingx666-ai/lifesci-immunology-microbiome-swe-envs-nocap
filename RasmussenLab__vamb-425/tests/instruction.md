# Issue

**Title:** Only drop_last with enough elements in data loaders

## Description

Some models in Vamb used dataloaders with `drop_last=True`. One rationale for this is that the last mini batch, having fewer elements, is likely to give inflated gradients, which will disrupt training.
However, since Vamb uses rather large batch sizes, this can easily result in a situation where the total number of observations is smaller than the batch size, which will result in an error, as no samples can be loaded from the dataset.

Here, we only set `drop_last` if there are more observations than one mini batch size.

Close #424

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2a05d68f528`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.