# Issue

**Title:** Fix sample trees and dendrograms in `anvi-compute-trnaseq-functional-affinity`

## Description

This PR fixes `--save-sample-trees` and `--plot-sample-dendrogram` in `anvi-compute-trnaseq-functional-affinity`. Whenever the clustered affinity table had a blank cell, the program failed with the error, "The condensed distance matrix must contain only finite values."

- Drop the samples in which a genome has no affinities from that genome’s tables, plots, and trees. With several genomes (`--internal-genomes`, `--external-genomes`, `-C`, or `-B`), the affinity table has a column for every sample in the run, so a genome had blank columns for the samples in which only other genomes have affinities. A genome’s `--separate-genomes` tables, plots, and sample trees now omit those samples, so they are identical to those of a run of the genome by itself. Tables that combine several genomes still have every sample, in the same order as before.
- Leave functions and samples without values out of sample clustering. A function that uses none of the codons decoded by the genome’s isoacceptors has no affinity in any sample. Normalized affinities are undefined in a sample where every function has the same affinity — the case with a single function.
- Skip a sample tree or dendrogram when fewer than two samples have values or some distances between samples are undefined. The plot is then drawn without the sample dendrogram, like for the codon dendrogram of a single function. A tree loaded with `--plot-sample-tree-file` is likewise not drawn when fewer than two samples have values.
- Skip the plot of a genome that has no values in any plotted sample, as can happen with `--select-samples-txt`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `28bda64e5297`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.