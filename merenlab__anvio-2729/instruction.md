# Issue

**Title:** Rework anvi-compute-trnaseq-functional-affinity: new affinity metric, per-isoacceptor contributions, and flexible references

## Description

This PR reworks `anvi-compute-trnaseq-functional-affinity`, the program that relates changes in the tRNA pool measured by tRNA-seq to the codon usage of genes and gene functions through a metric we call affinity. A positive affinity means that a sample's tRNA supply is better matched to a gene's codons than the reference tRNA supply, favoring translation of the gene in the sample versus the reference.

Highlights:

- A clearer, more robust affinity metric. Affinity is now the demand-weighted average change in tRNA supply between a sample and a reference — a differential, expression-based form of the tRNA Adaptation Index (tAI). This replaces the previous regression slope definition, which did not make sense given the dependence of slope not only on covariance (the current metric) but also variance of the chosen x-axis variable (tRNA supply or demand), and could behave erratically (for example, flattening genuine periodic signals in a time series).
- Per-isoacceptor contribution analysis through `--save-isoacceptor-contributions`. Each affinity can be broken into additive per-tRNA pieces, showing which isoacceptors drive a gene's affinity in each sample. Isoacceptor contributions can be summarized per sample, per gene, and overall.
- Flexible choice of reference. Sample tRNA supplies can be compared to a single reference sample (`-r`), a chosen group of samples (`--reference-samples`), or the mean of all samples (`--reference-mean`). Mean references are useful when no single sample is a natural baseline, as in a time series. The required `--nonreference-samples` option was renamed to `--analyzed-samples` given the possibility of overlap between samples for which affinity is calculated and samples used in the mean reference.
- Bacteria-appropriate decoding weights. Default tRNA wobble weights now come from the average of a set of bacterial genomes analyzed by Sabi and Tuller (2014). These are better suited to data likely to be processed by anvi'o than the wobble weights of dos Reis et al. (2004) derived from the yeast genome.
- Standard errors. Every affinity now carries a standard error reflecting how well coverage counts support it. An output option to normalize affinities and contributions by standard error (a z-score) facilitates the identification of robust patterns in across samples.
- Unit-test suite.
- Program artifact expanded, revised, and rewritten.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5bddc0e7d6a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.