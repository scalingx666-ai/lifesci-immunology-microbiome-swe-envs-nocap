# Issue

**Title:** New program: anvi-get-sequences-for-function-hits

## Description

This PR introduces a simple program that we needed since anvi'o was 3 years old.

It is as described in the help doc and obvious from the name: `anvi-get-sequences-for-function-hits`. It is similar to `anvi-get-sequences-for-hmm-hits`, but much less talented, as I described the reasoning behind it in the program help:

> (...)
>
> %(anvi-get-sequences-for-function-hits)s is very similar to %(anvi-get-sequences-for-hmm-hits)s, but unlike the latter, this program does not have any functionality to concatenate genes for downstream phylogenetic or phylogenomic analyses. While this was not difficult to implement, it was a mindful omission on our part. This is primarily due to the fact that genes that share a functional annotation can have extremely low sequence identity depending on the breadth of their representation in databases, so their sequences may not a reliable basis for phylogenetic or phylogenomic inferences even though it may not be immediately obvious for all functions. HMMs can also return not-so-ideal hits, but since they are built from aligned sequences by design, they are generally more appropriate to work with for such goals.
>
> (...)

_(If we want this program to also have that kind of talent, then we need to redesign a few things (implement a base class so HMM hits logic is not copy-pasta'd elsewhere unintentionally))_

I tested it and saw that it works as intended.

Now getting all AMR genes from a bunch of contigs-db files is two steps:

``` bash
# annotate
anvi-run-amrfinder -c contigs-db

# get sequences
anvi-get-sequences-for-function-hits -c contigs-db --annotation-source AMRFinder -o amr-genes.fa
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1990d03e4b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.