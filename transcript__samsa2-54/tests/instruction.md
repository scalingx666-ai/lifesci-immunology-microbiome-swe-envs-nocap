# Issue

**Title:** volcano_plot.R

## Description

R script to visualize differential expression between control and experimental metatranscriptomes. Takes a DESeq output file from the working directory and produces a volcano plot as a .pdf in the same directory. The R package EnhancedVolcano v1.4.0 (https://github.com/kevinblighe/EnhancedVolcano) needs to be installed beforehand on R v>3.6.1. Special characters (e.g. apostrophes) may be the source of issues with the labels on the plot. Also, need to find a way to fit the xlim in a better way.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `688079c74559`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.