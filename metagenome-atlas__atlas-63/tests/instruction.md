# Issue

**Title:** Improve assembly

## Description

first merge #60

@brwnj  I will merge when finished, but I'd like to have your input. 

- I split the function `align_reads_to_final_contigs` into two, to optimize the workflow.
- I clarified some of the parameters in `featureCounts`, e.g. what happen when one reads overlaps two genes. 


 When using the default treshold ( `CONTIG_MIN_ID=0.76`) all potential mapping positions above threshold are counted. Resulting in counting one read multiple times. The gene count have now a correction for this thanks to the `--fraction` param but the contig abundance are not corrected. And they are used for binning. 

Therefore I think that `CONTIG_COUNT_MULTI_MAPPED_READS=False` is better than `CONTIG_COUNT_MULTI_MAPPED_READS=True`. 

using `CONTIG_COUNT_MULTI_MAPPED_READS` one can define how ambiguous reads are handled in the two rules `align_reads_to_final_contigs` and `featureCounts`:
`CONTIG_COUNT_MULTI_MAPPED_READS=False` results in mapping only the best to the contigs and countig them. 

Alternative ways are possible, what do you think?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4faa17973f58`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.