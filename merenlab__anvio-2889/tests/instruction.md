# Issue

**Title:** Change affinity normalization in dealing with multiple genomes in `anvi-compute-trnaseq-functional-affinity`

## Description

This PR changes how `anvi-compute-trnaseq-functional-affinity` calculates affinity with several genomes (`--internal-genomes`, `--external-genomes`, or a collection with `-C` or `-B`). A genome's affinities used codon demands normalized to all of the genomes in the run, so that affinities depended on the entire set of genomes rather than being consistently calculated from the genome's codon usage in any context.

- Normalize the demand of each function or gene over the isoacceptors of its own genome. The table of isoacceptor codon weights has a column for each isoacceptor of every input genome, and each row was divided by its sum over all of these columns. Isoacceptors of other genomes, which never enter a genome's affinities, therefore diluted its demand. This scaled its affinities, standard errors, and isoacceptor contributions toward zero, to 41-59% of their single-genome values in test data. Demand now sums to 1 over the genome's own isoacceptors, and a genome gets the same results as in a run by itself.
- Blank the weights of isoacceptors that a row's genome lacks in `--save-isoacceptor-codon-weights` tables. These cells held weights that never entered the genome's affinities. Tables saved with `--separate-genomes` drop those columns, as in a run of the genome by itself. Genomes without affinities, such as those with fewer isoacceptors than `--min-isoacceptors`, are left out, so the table has the same rows as the affinity table.

Runs of a single genome are unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e05cce57038`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.