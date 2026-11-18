# Issue

**Title:** Allow taxonomy to contain filtered contigs

## Description

When parsing a Taxonomy object, each seq in the input file needs to be matched with the existing seq in the CompositionMetaData. However, seqs may be filtered from the latter, if they fall below the minimum length. So, when we encounter a seq in the taxonomy file not present in the composition, how do we know if it's invalid, or merely filtered?

We have the following (bad) options:
1. Use the refhashing mechanism, which requires the sequences are in the same order as in the composition. This is an extra constraint on the input file, which is a kind of breaking change (but unlikely to actually break anything)
2. Have a length column in the taxonomy file. This is clearly a breaking chnage, since input files will no longer work.
3. Skip any sequence not present in the composition, but then check that the taxonomy contained all the sequences in the composition. Thus, do less validation than would be optimal, but no breakage

This commit goes with option 3.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f27691adc4bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.