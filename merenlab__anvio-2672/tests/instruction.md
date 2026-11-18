# Issue

**Title:** anvi-summarize: adding --light-summary for reporting coverage but not bin info

## Description

## Summary 

Addition of a `--light-summary` flag specific to the profile version of `anvi-summarize`. The light summary reports minimal information about the bins (same behaviour as `--quick-summary`) but it reports all `bins_across_samples` view tables. It also reports `bins_summary.txt`, `misc_data_layers` and creates a mini html document. 

Relatedly, behaviour of `--quick-summary` was changed so it does not load the profile.db as it does not need to access coverage information. On the other hand, none of the changes made should impact `anvi-summarize` run on a pangenome database.

## Tests

The three `anvi-summarize` behaviors were tested on a dataset of 1920 MAGs (profile.db = 42G, contigs.db = 9.5G). On this dataset, the **full summary** took over 4 hours. The new implementation reduced the **quick summary** time from over an hour to 11 min with the longest step now being writing in the per-bin directories. Used memory was also reduced from ~60 Go to 16 Go. **Light summary** is very similar to the previous quick-summary implementation and took 47 min.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `afb2c01d0b39`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.