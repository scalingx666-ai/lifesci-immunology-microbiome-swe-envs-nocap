# Issue

**Title:** Add per-population copy number (PPCN) normalization to anvi-script-gen-function-matrix-across-genomes

## Description

I would like to compare functional capacities across metagenomic assemblies using individual functional annotations such as KEGG kofams or NCBI's COGs. But similar to estimating metabolic capacity, the problem when comparing assemblies rather than individual genomes is that each function is most likely present everywhere at least once in complex communities and different samples can contain very different number of populations, either for ecological reasons or differences in sequencing depth. So Iva came up with the per-population-copy-number (PPCN) normalization to be able to compare the metabolic capacities acros metagenomic assemblies by normalizing the frequency of metabolic pathway annotations using the estimated number of populations based on SCGs. I want to do the same thing for functional annotations in an automated way and therefore added a --per-population-copy-number flag to the 'anvi-script-gen-function-matrix-across-genomes' script. When you add the flag, the script generates an additional output with PPCN normalized frequencies of functional annotations of whichever kind you chose. 

Same as before, the population counts are estimated from single-copy core genes via anvi'o's NumGenomesEstimator (the mode of SCG hits per domain, summed across Bacteria, Archaea, and Eukarya). You need to provide an external-genomes file for this flag to work and the contig-dbs should contain metagenomic assemblies or long read metagenomes, in which case assembly probably wouldn't be strictly necessary. 

One little thing I changed is the column order that 'anvi-script-gen-function-matrix-across-genomes' generates. Currently, the 'key' is the first column, then the contig-dbs with their numbers and then, at the very end, you can find a column with the functional annotation. I think it makes more sense to have that in front as well, especially if you have a large set of contig-dbs. 

I created the code with the help of Claude AI

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29810ba5f651`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.