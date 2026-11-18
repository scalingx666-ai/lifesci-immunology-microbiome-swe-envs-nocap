# Issue

**Title:** Patch: Shift to mia version of scuttle function to aggregate rows by group

## Description

Hi!

This PR addresses issue 

I initially planned to replace scuttle::sumCountsAcrossFeatures with scrapper::aggregateAcrossGenes. However, the latter exclusively takes a list of sets as input and returns a list of row sums for each set. This differs from the current preferred inputs (factor vector) and outputs (directly the aggregated matrix). This would downgrade any eventual DelayedArray (and possibly) sparse matrices to normal matrices, which is not ideal.

Instead, I decided to leverage the [mia in-house function](https://github.com/microbiome/mia/blob/4c0be600df3a8a38537fdf59a3779ba696a8f07c/R/merge.R#L147) for aggregation which initially handled specifically NA cases. I think this solution has some benefits: it simplifies the code (one aggregation function instead of two), it reduces dependencies, and avoids downgrading DelayedArrays to base matrices.

As a side note, assays are currently agglomerated sequentially, but if relevant we could parallelise using `bpmapply` instead of `mapply`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `997852c97d11`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.