# Issue

**Title:** Bugfix: Check for zero TNFs before projection

## Description

Before, when creating the dataloader, we raised an error if any contigs had observed zero TNFs, since this would imply a sequence that was only composed of ambiguous nucleotides, and thus an uninformative sequence (and almost certainly also a mistake in the input).
However, since this check was in the data loader, the check happened on the *projected* TNF space, and so the check for a sum of zero was meaningless. Indeed, not only would this error not be triggered when an actual zero TNF seq was observed, it would be falsely triggered in the very unlikely even that a sequence's projected TNF summed to exactly zero.

 - cc @ChaoXianSen - to apply this bugfix on your current branch, you can simply delete the code in `vamb/encode.py` that raises the error.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9eec8f7b06de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.