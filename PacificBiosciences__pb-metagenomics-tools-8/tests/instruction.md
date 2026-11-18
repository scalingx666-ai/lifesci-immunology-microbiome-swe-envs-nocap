# Issue

**Title:** add circular/linear binning paths

## Description

Pull out circular and linear contigs, bin linear contigs with MetaBat2. Perform binning on full contig set as well. Treat all circular contigs as a bin. Merge the bins using DAS Tool. Provides an increase in total bins recovered, as well as prevents circular and nearly complete contigs from being mis-binned.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e20a214d6380`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.